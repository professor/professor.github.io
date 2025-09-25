---
layout: post
title: "Spaghetti Models Part 5: Safely Remove ActiveSupport Concerns"
image: /images/spaghetti-five.jpg
date: 2023-09-27 21:45
comments: false
categories: Spaghetti Model 
---

# Spaghetti Models Part 5: Safely Remove ActiveSupport Concerns

Note: This is one part of my journey to tame a spaghetti model or god object. Start with [Post 1: Unraveling a Spaghetti Model](/toddsedano/2023/07/27/unraveling-a-spaghetti-model.html) to see how I chose to tackle this problem.

Your spaghetti model has been a dumping ground of methods and associations for years. In our case, it’s the company model. We know we need to add functionality to the system, so we place the new capability on the company because it’s convenient. We may rationalize it with “Besides, the company should know whether it has active medical benefits.”

## Overview
To deal with models with way too many methods, Rails 4 introduced ActiveSupport Concerns as a way of partitioning and reusing model code. Methods and associations that worked together could be extracted into a Concern.

While this made the code more manageable in the short term, each spaghetti model still had the same number of methods. Further, these concerns may or may not be good abstractions. Instead, we’d like to move domain logic into domain APIs.

## An Example
Here is an example ActiveSupport::Concern, the company model now has the method `company.origination_bank` , the association `company.payer_origination_banks`, and a lifecycle callback `setup_banking!` that is called each time the company is saved.

```ruby
def company
   include GustoBankAccountable
end

module GustoBankAccountable
  extend ActiveSupport::Concern
  extend T::Sig

  included do
      has_many(:payer_origination_banks)
      after_commit :setup_banking!, on: :create      
  end

  def origination_bank
   …
  end

  def setup_banking!
  …
  end
end
```
Analysis
List all of the active support concerns and identify which contain domain logic that should be moved to other packs.
```markdown
| Concern                               | Decision           | # Models |
|---------------------------------------|--------------------|----------|
| Sluggable                             | Stay               |        1 |
| Bank Accountable                      | Move to domains    |        1 |
| Analytics:Identifyable                | Unused so deleted  |        2 |
| PaymentsAndFilingsReschedulable       | Move to payments   |       15 |
| RiskAssessable                        | Move to risk       |        1 |
| BankAccountable                       | Move to payments   |        2 |
| AttrSquishable                        | Stay               |       14 |
| CompanyFormsObserver                  | Move to forms      |        1 |
| CompanyOnboardingFunnelUpdateable     | Move to onboarding |        5 |
| ZensaObserver                         | Stay               |       36 |
| AttrBoolean                           | Stay               |       27 |
| DirtyNestedAttributes                 | Stay               |       14 |
| AttrMemoized                          | Stay               |       49 |
| ExternalIdentities::IdentityDeletable | Stay               |        4 |
```

2. Start with active support concerns that are used by 1 model.

## Action
Our goal is to move or remove all the methods, associations, and lifecycle callbacks in the ActiveSupport::Concern.

Steps

For each method in the ActiveSupport::Concern, identify where it should live and then follow the techniques in [Part 3](/toddsedano/2023/07/28/spaghetti-models-safely-remove-methods.html)
2. Move active model lifecycle methods to the model. You can remove the concern now and deal with lifecycle methods later.

```ruby
# company.rb
has_many :payer_origination_banks, as: :payer, dependent: :destroy

after_commit(on: :create) do
  Payments::Banking::PayerOriginationBanks.setup_banking!(payer: self)
end
```
3. When all that is left is an empty concern, let’s celebrate! 🎉
```ruby
module GustoBankAccountable
  extend ActiveSupport::Concern
  extend T::Sig

  included do
  end
end
```
It’s time to say goodbye. 👋

Summary
Tackling an ActiveSupport::Concern is the same as handling methods, associations, and lifecycle callbacks.
