---
layout: post
title: "Rethinking regex"
date: 2010-11-18 12:13
comments: false
categories: [Software Engineering]      
alias: [/journal/2010/11/18/rethinking-regex.html]
---
                                                                      
What if regular expressions were easy to write?

While attending the Golden Gate Ruby Conference 2010, I attended a session about Arel and how Rails was changing their ORM layer to make it easier to incrementally build the query.

Old: Article.find(:all, :order => "published_at desc", :limit => 10)  

New: Article.order("published_at desc").limit(10)  

It occurred to me that this concept of simplifying could be applied to regular expression. 

While I have time, I'll continue to build up examples of what the syntax could look like.

 

Random thoughts:

What: not a number 

* ie a string that can't be convert to a number
* A string that contains at least on character 
* Regex: /^.*\D+.*$/
* Positive examples: 113t23io10908-113
* Negative examples: 13431