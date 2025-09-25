---
layout: post
title: "Spaghetti Models Part 4: Safely Remove ActiveRecord Associations and Scopes"
image: /images/spaghetti-four.jpg
date: 2023-08-30 21:45
comments: false
categories: Spaghetti Model 
---

# Spaghetti Models Part 4: Safely Remove ActiveRecord Associations and Scopes

Note: This is one part of my journey to tame a spaghetti model or god object. Start with [Post 1: Unraveling a Spaghetti Model](/toddsedano/2023/07/27/unraveling-a-spaghetti-model.html) to see how I chose to tackle this problem.

Your spaghetti model has been a dumping ground of methods and associations for years.

## Overview
In your journey to detangle a spaghetti model, you may come across ActiveRecord associations that you are pretty sure aren’t getting used, but you want to add a deprecation warning just in case you are wrong.

Rails makes it easy to have a model access all of its related entities through `belongs_to`, `has_many` and `has_one` helpers. These convenience methods allow us to quickly prototype and build new features. Rails and AREL make it easy for your models to navigate across database relationships. Gone are the days of writing lots of SQL to get a website up and running. However, with this power comes a cost. It’s too easy for an object to reach across domain boundaries and use methods of a distant object.

## An Example
Consider this example:

`company.funding_methods.payroll.reverse_wire.verified.default.first.present?`

Should a company really be able to access its reverse_wires through funding_methods and payrolls? Nope! In our system, this chaining is breaking the boundaries of different domains.

The associations allow us to easily reach through many objects to talk to use a method on our neighbor’s neighbor’s neighbor’s method. This anti-pattern is called a Law of Demeter violation.

## Strategy
Step 1: Remove all callers of the association or scopes.

Step 2: Add a method with the same name as the association or scope with a deprecation warning.

Step 3: Fix any failing tests.

Step 4: Deploy, wait, and verify that it’s not used in production.

Step 5: Remove the deprecated association or scope and the method you added in Step 2.

## Example 1: Simple example
Here we have a fraud scope that we would like to remove:

```ruby
# existing code
class Company < ApplicationRecord
    scope :fraud, -> { where(risk_state: FRAUD_STATES) }
end
```
We simply add an override method that calls a deprecation warning.

```ruby
# updated code
class Company < ApplicationRecord
    scope :fraud, -> { where(risk_state: FRAUD_STATES) }

    def self.fraud
      ActiveSupport::Deprecation.warn("Company.fraud at #{caller}")
      super
    end
end
```
This technique works for `has_many`, `has_one`, `belongs_to`, and scopes.

```ruby
class Company
  has_many :payroll

  def payrolls
    ActiveSupport::Deprecation.warn("Use Payroll.where(company_id: id) 
instead of company.payrolls at #{caller}")
    super
  end

  def payrolls=(value)
    ActiveSupport::Deprecation.warn("Use Payroll.where(company_id: id) 
instead of company.payrolls= at #{caller}")
    super(value)
  end
end

# usage
payrolls = Payrolls.where(company_id: company_id)
```

## Dependent Destroy
If your association has a dependent destroy, remove the destroy first, then do the simple association listed above.

```ruby 
# existing code
class Company
   has_many :risk_reviews, dependent: :destroy,
end
```
We extract out a destroy a destroy_associated_risk_reviews method.
```ruby
# updated code
class Company
  has_many :risk_reviews

  before_destroy :destroy_associated_risk_reviews

  def destroy_associated_risk_reviews
    RiskReviews.where(company_id: id).destroy_all
  end
end
```
After we have removed our associations, we would move the destroy_associated_risk_reviews method to the domain pack that contains RiskReviews. In our case, this would be our risk pack. When a company is deleted, we use an event system to notify the risk pack to delete its risk reviews. The event system would enqueue a sidekiq job that deletes risk reviews for a particular company.

```ruby
module RiskReviews
  class CompanyDeleted

    sig { params(company_id: Integer).void }
    def perform(company_id)
      RiskReviews.where(company_id: company_id).destroy_all
    end
  end
end
```

## Example: Polymorphic Relationships
This is a little more nuanced for a polymorphic relationship. The payer_origination_bank has two columns to represent the polymorphism: payer_id (which is a foreign key to the company, etc) and payer_type (which represents the name of the model, Company, etc).

```ruby
# existing code
class Company
   has_many :payer_origination_banks, as: :payer
end

# usage
company = Company.find(company_id)
banks = company.payer_origination_banks
```
We could replace `company.payer_origination_banks` with ``PayerOriginationBank.where(payer_id: companyid, payer_type: Company)`, however, that’s hard to read and odds are we’ll forget to pass in payer_type at some point. We’d like the usage to be something simple like `PayerOriginationBank.by_company_id(company_id: id)`, so let’s add a scope.

```ruby
# updated code
class Company
   has_many :payer_origination_banks, as: :payer

  def payer_origination_banks
    ActiveSupport::Deprecation.warn("Use PayerOriginationBank.by_company_id(company_id: id) instead of company.payer_origination_banks at #{caller}")
    super
  end

  def payer_origination_banks=(value)
    ActiveSupport::Deprecation.warn("... instead of company.payer_origination_banks= at #{caller}")
    super(value)
  end
end

class PayerOriginationBank
  scope :by_company_id, -> (company_id) do
    where(payer_id: company_id, payer_type: Company.name)
  end
end

# preferred usage 
PayerOriginationBank.by_company_id(company_id: company_id)
```

## Example 2: Complex Association
This technique works with complicated associations. Consider this example:

```ruby
# existing code
class PaymentRecord < ApplicationRecord
  belongs_to(
    :company,
    -> do
      includes(:payment_records).where(payment_records: { on_behalf_of_type: Company.name })
    end,
    class_name: :Company,
    foreign_key: :on_behalf_of_id,
    optional: true
  )
end
```
We can simply add a deprecation method:

```ruby
# updated code
class PaymentRecord < ApplicationRecord
  ...

  def self.company
    ActiveSupport::Deprecation.warn("PaymentRecord.company at #{caller}")
    super
  end
end
```

## Summary
By adding override methods with deprecation warnings, we can verify that a scope or association is no longer used and is safe to delete.
