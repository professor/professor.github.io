---
layout: post
title: "Spaghetti Models Part 3: Safely Remove Methods"
image: /images/spaghetti-three.jpg
date: 2023-07-28 21:45
comments: false
categories: Spaghetti Model 
---

# Spaghetti Models Part 3: Safely Remove Methods

Note: This is one part of my journey to tame a spaghetti model or god object. Start with [Post 1: Unraveling a Spaghetti Model](/toddsedano/2023/07/27/unraveling-a-spaghetti-model.html) to see how I chose to tackle this problem.

Your spaghetti model has been a dumping ground of methods and associations for years. In our case, it's the company model. We know we need to add functionality to the system, so we place the new capability on the company because it's convenient. We may rationalize it with "besides, the company should know whether it has active medical benefits."

Except in our case, we are building for at least two different business domains. We created some companies for payroll and other companies for benefits. Instead of piling domain logic onto the company, we need to move payroll concepts into payroll classes and benefits concepts into benefits classes.

## Overview
Here I'll present four cases for simplifying your spaghetti model's methods…
  * Methods that are dead code.
  * Methods that wrap existing public APIs.
  * Methods that need a public API.
  * Methods that need a public API and return a value object instead of a model - that way, we aren't passing around Active Models through our APIs.

## Safely Remove Unused Method
With an older code base, you might have several unused methods. Let's remove the dead code first. After you sleuth around your code base, you might be sure it's safe to delete the method. In our code base, we had some fun meta-programming tricks. Since our spaghetti model is used everywhere, I wanted to be really, really certain the code was unused. I added an ActiveSupport::Deprecation.warn to be extra careful.
```ruby
# existing code
class Company < ApplicationRecord
  def api_onboarding?
    !!api_onboarding
  end

  def household_employer?
    false
  end
end

# updated code
class Company < ApplicationRecord
  def api_onboarding?
     ActiveSupport::Deprecation.warn("Company.api_onboarding? is deprecated at #{caller}")
     !!api_onboarding
  end

  def household_employer?
     ActiveSupport::Deprecation.warn("Company.household_employer? is deprecated at #{caller}")
    false
  end
end
```
Deploy the new code to production. Then wait for what you think is a reasonable amount of time. Double-check the logs that the method isn't used, and then remove it.

👋 Adios!

## Spaghetti Model: Safely Inline Wrapper Method
Refactor type: inline method

A spaghetti model can have many convenience methods. We've grown accustomed to loading the company model first and then accessing all sorts of associations and business logic from it. Instead, we can load that information directly without bothering the company model.

Let's look at an example:
```ruby
# existing code
class Company
  def addresses
    Addresses.for_company(company_id: id)
  end
End

# usage
addresses = Company.find(company_id).addresses
```
Here, we have a convenience method `company.addresses` that simply wraps the Address public interface. In this production code example, notice that we do an unnecessary query to the database and load a company model solely for the purpose of using the convenience method.

The solution is pretty simple. We delete the convenience method and then call the Address public API directly.
```ruby
# new code
class Company
  def addresses
    ActiveSupport::Deprecation.warn("Use Address.for_company instead of company.addresses at #{caller}")
    Addresses.for_company(company_id: id)
  end
end

# usage
addresses = Addresses.for_company(company_id: company_id)
```

**Steps**
  1. Look for each usage of `company.addresses` and inline them. For a popular method, feel free to do this in multiple pull requests.
  2. Add a warning method, push to CI, and see if anything breaks. `ActiveSupport::Deprecation.warn('Use <new API> instead of <old API>')`
  3. Remove the method when it's safe to do so. In our context, we need to wait two weeks just to be safe that no meta-programming code is using it.

**Time investment**

Most of my time was spent updating tests that failed in unexpected ways. Some time was spent on modifying GraphQL to use public APIs instead of spaghetti model methods. In a few cases, I moved tests from the spaghetti model specs to the public API specs.

## Spaghetti Model: Safely Extract New Public APIs
**Extract domain API by moving a method out of your spaghetti model**

Refactor type: Move method

For the win: In our code base, we moved 47 methods using this technique.

This first example is very small, but you could easily imagine a much longer method. I certainly saw them. ;)

The "move method" technique appears similar to the "inline method" technique, however, the code we want to inline is not a public API. We create a new public API from the existing method.
```ruby
# existing code
class Company
  def has_active_medical_benefits?
    benefits.active.medical.any?
  end
end

# usage
company.has_active_medical_benefits?
```
I created a new public API on the payroll_benefits class. I then changed all known callers to use the new public API.

Because we have metaprogramming in our codebase, I will not delete the method for a few weeks. Adding the deprecation reminds other developers not to use the original method.

```ruby
# new code
class Company
  def has_active_medical_benefits?
    ActiveSupport::Deprecation.warn("Use PayrollBenefits.has_active_medical_benefits?() instead of company.has_active_medical_benefits?()")
    benefits.active.medical.any?
  end
end

class PayrollBenefit
  def self.has_active_medical_benefits?(company_id:)
    Benefit.active.medical.where(company_id: company_id).any?
  end
end

# usage
PayrollBenefit.has_active_medical_benefits?(company_id: company.id)
```


**Steps**
  1. Create a new public API.
  2. Look for each usage of `company.has_active_medical_benefits` and replace it with a call to the public API. For a popular method, feel free to do this in multiple pull requests.
  3. Add a warning method, push to CI, and see if anything breaks. `ActiveSupport::Deprecation.warn('Use <new API> instead of <old API>')`
  4. Remove the method when it's safe to do so. In our context, we need to wait two weeks just to be safe that no meta-programming code is using it.

Here's a more interesting example of memoization.
```ruby
# existing code
class Company
  def has_fsa_dependent_care?
    @has_fsa_dependent_care ||= benefits.by_type(BENEFIT_TYPE_DEPENDENT_CARE_FSA).exists?
  end
end

# usage
company.has_fsa_dependent_care?
```
You'll want to audit your code to see how important the memoization is. In this case, the method is used inside a background Sidekiq worker, so it was safe for me to remove it. Otherwise, the caller code will need to store the value in its object. Remember to not memoize values that change.
```ruby
# new code
class PayrollBenefit
  def self.has_fsa_dependent_care?(company_id:)
    Benefit.by_type(BENEFIT_TYPE_DEPENDENT_CARE_FSA).where(company_id: company_id).exists?
  end
end

# usage
PayrollBenefits.has_fsa_dependent_care?(company_id: company.id)
```

## Spaghetti Model: Safely Extract New Public APIs with Value Objects
In the following case, I noticed that the callers of the code wanted to access attributes of the PendingCompanySuspension model. We've decided not to pass ActiveModels across our APIs but to use value objects instead. If we returned an ActiveRecord model, then the caller could call any association or method on the object.
```ruby
# existing code
class Company
  sig { returns(T.nilable(PendingCompanySuspension)) }
  def effective_pending_company_suspension
    ActiveSupport::Deprecation.warn('Use PendingCompanySuspension.active.where(company_id: company.id).first instead of company.effective_pending_company_suspension')
    active_pending_company_suspensions.first
  end
end

# usage
status = company.effective_pending_company_suspension.suspension_status
```
```ruby
`# new code
module PendingCompanySuspensions
  class ValueObject < T::Struct
    extend T::Sig
    include TypedStructHelper

    const :id, Integer
    const :failure_type, T.nilable(String)
    const :reason, T.nilable(String)
    const :suspend_on_date, Date
    const :company_id, T.nilable(Integer)
    const :agent_name, T.nilable(String)
    const :agent_state, T.nilable(String)
    const :suspension_status, String

    sig { returns(T::Boolean) }
    def should_payroll_be_blocked?
      Time.zone.today >= suspend_on_date - PendingCompanySuspension::PAYROLL_IS_BLOCKED_PERIOD.days
    end
  end
end

module PendingCompanySuspensions
  extend T::Sig

  # Find first effective Pending Company Suspensions based on company_id
  # Returns nil if not found
  sig { params(company_id: Integer).returns(T.nilable(PendingCompanySuspensions::ValueObject)) }
  def self.effective(company_id:)
    active(company_id: company_id).first
  end

  # Private method that converts a PendingCompanySuspension to PendingCompanySuspensions::ValueObject
  sig { params(pending_company_suspension: PendingCompanySuspension).returns(PendingCompanySuspensions::ValueObject) }
  def self.to_identity_object(pending_company_suspension)
    PendingCompanySuspensions::ValueObject.new(
      id: pending_company_suspension.id,
      failure_type: pending_company_suspension.failure_type,
      reason: pending_company_suspension.reason,
      suspend_on_date: pending_company_suspension.suspend_on_date,
      company_id: pending_company_suspension.company_id,
      agent_name: pending_company_suspension.agent&.name,
      agent_state: pending_company_suspension.agent&.state,
      suspension_status: pending_company_suspension.suspension_status
    )
  end
  private_class_method :to_identity_object
end

# usage
PendingCompanySuspensions.effective(company_id: company.id).suspension_status
```

**Steps**
  1. Create a value object
  2. Create a public API
  3. Leverage public API

**Time investment**

Most of my time was spent updating tests that failed in expected ways. Some time was spent on modifying Graphql to use public APIs instead of private model calls. In a few cases, there were tests of the convenience method that I moved to test the public API.

## Summary
When removing methods from a spaghetti model, there are several refactoring techniques that we can use including inline method, move method, and extract as public API.
