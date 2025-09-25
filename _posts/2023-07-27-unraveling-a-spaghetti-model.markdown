---
layout: post
title: "Unraveling a Spaghetti Model"
image: /images/spaghetti-one.jpg
date: 2023-07-27 21:45
comments: false
categories: Spaghetti Model 
---

# Unraveling a Spaghetti Model

In many established Ruby on Rails applications, there are often a couple of classes that become entangled with the rest of the code base. These early models start small and simple, possibly present for the first commit, but over time, the rest of the code base becomes entangled with them.

Some call them god objects (omniscient or all-knowing objects) since they reference a large number of other objects and often have unrelated methods. It's a well-known anti-pattern or code smell [1996 Reference](https://amzn.to/3uijk3p).

In Gusto's [journey](https://medium.com/gusto-engineering/laying-the-cultural-and-technical-foundation-for-big-rails-6b5ab78349ed) to create a modularized monolith, we leverage [Packwerk](https://github.com/Shopify/packwerk) to move domain concepts into packs. For example. we created a `payments` pack and then moved all the models, controllers, views, services, and specs needed for that domain. With all the code in packs, we created a public API for the rest of the code to access that domain's interface. What's left are our "spaghetti" models. They are called spaghetti models because they are entangled with all the domain's code (via associations) and contain domain code (via methods) that belong somewhere else. In this blog series, I'll share how I tackled our largest spaghetti model.

**Tackling spaghetti models can feel overwhelming.** It took years for them to form and untangling the mess can feel like a Gordian knot with no clear starting place. At Gusto, we have two main spaghetti models: company and employee. When I first started untangling the company spaghetti model, I didn't know where to start. The other members of my team were concerned about whether we could even tackle the problem. Here's a class with 11 years' worth of experience, 408 methods, 195 associations, and 51 columns. Engineers on other teams are afraid to touch it: "If you modify it, it might break our business-critical payroll. It's so entangled."

So with a bit of audacity, naivety, and experience, I picked up my chisel and slowly started chipping away at it. We know from [Angela Duckworth's book](https://www.amazon.com/dp/1501111116/ref=cm_sw_r_as_gl_api_gl_i_G2RD1G57FQ9KTB2F4DTV?linkCode=ml2&tag=sedano-20), that grit is the secret to outstanding achievement. Fortunately, I kept chiseling away at our spaghetti model.

<img border="0" src="/images/company-model-methods.png" alt="Graph showing number of methods growing over time"/>
Number of company model methods over time

**This is the story of my journey.** These techniques worked well for us. I wanted a safe removal and refactoring of code without breaking the system. Feel free to try the techniques in a different order and let me know about your journey.

**Objective: Move domain concepts into domain modules.** In our system, the Company model represents a business that wants to use our products. Ideally, our Company model would only contain code related to the company's identity (business name, tax number, legal trading name, id). However, most of the stuff on the Company model was domain concepts that belong in different modules or packs. In our project, we split our codebase into packs with private and public APIs (see [Ruby At Scale](https://github.com/rubyatscale) for more information). My refactors then moved methods from the company or its concerns to domain packs. Our long-term goal is a slim company model that is only identity information.

**Objective: Clean boundaries.** In our ideal system, public APIs return simple ruby objects so that client code can not leverage associations and other Ruby on Rails convenience methods. Private APIs can return ActiveRecord models. Code calling other domains should use public APs. Instead of passing a company rails model around, we pass a company_id or a company value object.

<img border="0" src="/images/company-model-associations.png" alt="Graph showing number of associations growing over time"/>
Number of company model associations over time

## Goal 1: Prevent the model from getting worse
Our first step is to write tests to prevent other developers from adding more methods, associations, and columns. See [Add Tests To Stop the Growing Spaghetti Model](/toddsedano/2023/07/28/spaghetti-models-add-tests-to-stop-the-growing-spaghetti-model.html) for details.

Honestly, I didn't start here, but once I noticed that other developers were still adding to the company model, we wrote some tests. The tests provide an automatic feedback mechanism for developers.

## Goal 2: Examine the database
I started with an audit of the model. I skimmed through each method, trying to see where to start. After the read-through, I then looked at the database columns. I noticed that some of these had not been written in years. I chose to clean up our database table before taking anything else. After getting familiar with the columns, I then removed dead methods and started inlining the code. See [Safely Removing Dead Columns](/toddsedano/2022/11/17/rails-spaghetti-model-delete-column-tutorial.html) for details.

## Goal 3: Move domain logic to domain packs
Shrinking a spaghetti model is removing all the code that doesn't belong there. A typical ActiveRecord Model will have:
  * columns
  * methods
  * associations (has_many, has_one, belongs_to)
  * lifecycle callbacks (after_create, before_save, …)
  * validations
  * ActiveSupport::Concerns
  * mixins 
  * delegated methods
  * scopes

My job was to remove all the junk that didn't belong there.

### What to work on first?
I went through the spaghetti model and moved domain logic into domain packs. After moving some methods, associations, and callbacks, I found that some refactors were simpler than others. From easiest to hardest:
  1. methods are the easiest
  2. ActiveSupport::Concerns (*)
  3. infrequently referenced associations
  4. lifecycle callback methods
  5. columns
  6. frequently referenced associations are the hardest, and it may be that we'll never remove all of them

(*) Since ActiveSupport::Concerns serve as inline code, they can contain methods, associations, and lifecycle callbacks. To address ActiveSupport::Concerns, I used the same tactics for addressing methods, associations, and lifecycle callbacks.

### Tactics
A spaghetti model is a collection of methods, associations, scopes, call-backs, and delegated methods. For each of these, I wrote a blog post on how I handled them:

A. Dealing with methods [Part 3](/toddsedano/2023/07/28/spaghetti-models-safely-remove-methods.html)
  * Safely remove dead methods
  * Safely inline wrapper method
  * Safely extract new public APIs
  * Safely extract new public APIs with value objects

B. Dealing with Active Model [Part 4](/toddsedano/2023/08/30/spaghetti-models-safely-remove-active-record-associations-and-scopes.html)
  * Safely remove scopes
  * Safely remove associations

C. Dealing with ActiveSupport::Concerns [Part 5](/toddsedano/2023/09/27/spaghetti-models-safely-remove-active-support-concerns.html)
  * Safely remove active concerns (see other techniques)
  * Sleuthing

D. ActiveAdmin [Part 6, coming soon]
  * Creating another model for ActiveAdmin ransack methods (coming soon)

### Tracking Deprecations
In each of the safe techniques listed in the Tactics section, I leveraged ActiveSupport::Deprecation.warn to verify that the method or association or lifecycle callback was no longer used in production. I would wait until I felt it was safe to remove the code from the system. To help me track my merged deprecation warnings, I used a simple spreadsheet.

```markdown
|------------|------------------|--------------------|--------------------|
| Date Added | Class            | added by           | removed by         |
|------------|------------------|--------------------|--------------------|
| 2023/06/14 | company          | <pull request url> | <pull request url> |
| 2023/06/15 | company          | <pull request url> | <pull request url> |
| 2023/07/01 | company          | <pull request url> |                    |
| 2023/07/15 | bank_accountable | <pull request url> |                    |
|------------|------------------|--------------------|--------------------|
```
Whenever I had a few minutes between meetings, I'd look at this table to see if any deprecated methods or associations were ready to be deleted. I then checked DataDog to verify that nothing had used the method in the last few weeks. I'd then remove the code for good.

<img border="0" src="/images/spaghetti-one-end.jpg" alt="Picture of a Train"/>

## Conclusion
By following popular and espoused Ruby on Rails patterns, and with a lack of investment in deliberate work on architecture, long-lived code bases foster spaghetti models. In this blog post, I provide a top-level strategy for tackling spaghetti models with follow-up blog posts digging into specific tactics.

In time, your code base will have less chaos and will be humming along.
