---
layout: post
title: "Removing dead columns"
image: /images/spaghetti-roman-column.jpg
date: 2022-11-17 21:45
comments: true
categories: Spaghetti Model 
---

# Cleaning House - Removing dead columns

On January 10, 2023, our code base turns 11 years old. For a repo with this much history, we’d expect for the business needs and features to have evolved over time. Surely in the quest to ship new features, our past selves might have forgotten to remove all the dead code. While examining our spaghetti model, we were trying to figure out the purpose of each item. Some of this analysis is waste since the column might be dead code.

## Explore your table

We have many nullable columns, so I was curious if any of them were no longer used. For each column, I ran this query

```
select id, created_at from companies where name IS NOT NULL ORDER BY id DESC  LIMIT 1;
```

I came across five columns that were very old

column                       | Last created company to have this value set (1)
------------------------|--------------------------------------------
code           | 2015-08-18 15:15
industry              | 2017-05-19 18:52
special_code        | 2015-08-18 15:15
zendesk | 2018-05-10 10:43
google         | 2018-05-16 16:12

## Research the history of the column

This is strong evidence that the column isn’t getting used. I do like to look around a bit more to see what’s up.

1. Check out the migrations
2. `git log -S special_code`

The extra research allowed me to see when it was added. Several of the columns were added together, and when they were no longer used by the code. It also gave me a list of people to possibly talk to if I had more questions.

# 1. (Optional) Fail Your Tests
See which tests fail if your column is removed. Don’t forget to turn off any validations!

```
  self.ignored_columns = [

:special_code,
  ]	

# validates :special_code, inclusion: { in: SPECIAL_CODES}, allow_blank:true
```

I learned that we had a `.rabl` file that displayed the `special_code` which caused many tests to fail. I then removed it from the `.rabl` file and re-ran my tests.

It’s possible that you can just skip this step. I had noticed that there were many references to `special_code` in my tests and I was concerned that removing them would leave an unexposed usage of `special_code`. However, we have that covered later on by adding Step X, logging.

# 2. Remove any dependent dead code

If the column is dead, there might be additional dead code that needs removing. Have fun!

# 3. Introduce logging to make sure nothing is using the attribute / column

I’ve been burned by meta-programming. If this table is in the center of all the action, taking a few extra steps is worth giving you the confidence that nothing is going to fall apart in the next step. Any issues will be a log statement.

```
  def special_code
    Rails.logger.info("Using Company#special_code at #{caller}")
    super
  end

  def special_code=(code)
    Rails.logger.info("Using Company#special_code=  at #{caller}")
    super(code)
  end
```


After deploying, I then wait a day (or longer) to see if there is hidden part of the system using the code. You might just be surprised!

# 4. Mark the column as unused or ignored by rails
It’s tempting to jump to the migration. In large rails systems, it’s a best practice to never rollback a migration. This is our last line of defense before dropping the column for real. Any issues will cause a rails exception.

```
self.ignored_columns = [:special_code]
```

Remove the logging that you added in the previous step
```
-  def special_code
-    Rails.logger.info("Using Company#special_code at #{caller}")
-    super
-  end

-  def special_code=(code)
-    Rails.logger.info("Using Company#special_code=  at #{caller}")
-    super(code)
-  end
```

If you use any tools to annotate your model, these should remove all the annotations as well.

# 5. Delete the column with a migration

```
bin/rails g migration DropSpecialCodeColumnFromCompany
```

Look at your `db/schema.rb` file for any indexes. I go here to seee the column type and defaults for the down method (even though it will never be run on my production systems)

```
rake db:migrate
```

If you use a system like ghost, this will generate the json changes too.

# 6. Clean-up

After you’ve run the migration in all environments, now it’s time to take care of any cleanup. Remove the `self.ignored_columns` from your model.
