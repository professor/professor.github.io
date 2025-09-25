---
layout: post
title: "Spaghetti Models Part 2: Add Tests to Stop the Growing Spaghetti Model"
image: /images/spaghetti-two.jpg
date: 2023-07-28 21:45
comments: false
categories: Spaghetti Model 
---

# Spaghetti Models Part 2: Add Tests to Stop the Growing Spaghetti Model

Note: This is one part of my journey to tame a spaghetti model or god object. Start with [Post 1: Unraveling a Spaghetti Model](/toddsedano/2023/07/27/unraveling-a-spaghetti-model.html) to see how I chose to tackle this problem.

## Overview
Your spaghetti model has been a dumping ground of methods and associations for years. All of your developers have built up muscle memory to continue to add to it. Let's provide a gentle reminder for everyone to stop our existing behavior.

**We'll add tests to prevent the addition of associations and methods.**

You'll want to lock down permissions to this test file, thus requiring GitHub PR approval from your team for modifications to the tests. While others might be initially annoyed that they can't keep adding to the dumping ground, at least they have been informed that there's a new way to do this. Feedback is a gift. 🎁 What's cool is that you don't have to be the person doing the nagging, the tests will do it on your behalf. These tests then are double gift 🎁 🎁.

## The Tests
Let's write a test that prevents developers from adding new columns:

```ruby
RSpec.describe Company do
  let(:company) { create(:company) }

  # We're preventing developers from adding more our company spaghetti model. 
  # Instead, consider adding an API to your domain, and using that instead. 
  # Perhaps it takes company_id as the input 

  # To put it in terms of dependencies -- this model shouldn't depend on 
  # the idea of your domain. Instead, your domain should depend on company.

  it 'does not have any new columns' do
    existing_columns = %w(
      id
      name
      trade_name
      <skip 40 more>
      uuid
    )
    new_columns = Company.columns.map(&:name) - existing_columns
    expect(new_columns).to be_empty
  end
end
```
Let's write a test that prevents new associations from getting added:
```ruby
RSpec.describe Company do
  let(:company) { create(:company) }

  it 'does not have any new associations' do
    existing_associations = %i(
      banks
      users
      roles
      <skip several hundred>
      calendars
    )
    new_associations = Company.reflect_on_all_associations.map(&:name) - existing_associations
    expect(new_associations).to be_empty
  end
end
```
Let's write a test that prevents developers from adding new methods:
```ruby
RSpec.describe Company do
  let(:company) { create(:company) }

  it 'does not have any new methods' do
    existing_methods = %w(
      verified?
      suspended?
      as_json
      to_param
      <skip several hundred>
      verify_ein
    )
    current_methods = []
    File.open('packs/company_spaghetti_model/app/models/company.rb').each do |line|
      match = line.match('def ([\w?!=\.]*)')
      if match && match[1] != ''
        current_methods << match[1]
      end
    end
    new_methods = current_methods - existing_methods
    expect(new_methods).to be_empty, 'Do not add more methods to the Company model, create a public API on a domain pack.'
  end
end
```
Yes, there's probably a fancier way to assert for methods getting added =)

Note that this won't prevent people from adding more junk to the included ActiveSupport::concerns, but at least you've stopped people from making the main spaghetti model worse.

Thank you to [Alex Evanczuk](https://medium.com/u/bffa4a615a1b?source=post_page---user_mention--26afde018ebe---------------------------------------) for writing our first association tests.

## Summary
At the start of our journey to unravel the spaghetti model, the first step is to automatically let other developers know that the spaghetti model is no longer our dumping ground of methods and associations. We leverage our test suite to add purposeful friction to the development process.
