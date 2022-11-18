---
layout: post
title: "Transitioning from MySQL to Postgresql"
date: 2010-06-22 12:11
comments: false
categories:                                                                     
alias: [/journal/2010/6/22/transitioning-from-mysql-to-postgresql.html]
---

Postgresql doesn't marshal data types like MySQL does. For many of my tables, I store year as an INTEGER. In one of my tables, when I did the migration, I specified it as a VARCHAR. This generated this error.

PGError: ERROR: operator does not exist: character varying = integer\nLINE 1: ...n_id = u.id)

Solving it was pretty simple. In my development and production databases I did the following commands. Then did a new data push to heroku's postresql database.

1) Create another column using the MySQL Administrator GUI tool. Ie year2 of type INTEGER

2) Run the following command from MySQL Query Browser "update courses set year2 = year"

3) Drop the column year.

4) Rename column year2 to be year.5) heroku db:push mysql:...

There are good documents here: http://docs.heroku.com/database