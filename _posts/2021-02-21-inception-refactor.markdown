---
layout: post
title: "Inception Refactor"
date: 2021-02-28 07:36
comments: true
categories: Refactoring 
---

While working on a feature or a refactor, sometimes we wished that the code looked differently. A developer might think, "If only the code than this interface or this structure, then my work would be easier." When this happens, we could either do all the refactorings at once or sequence the work with an Inception Refactor. 

Here are the steps:
   * We stash or hide all the changes we've made, placing us back into a green state.
   * We make the modification we wish we had.
   * We verify that the tests are all green.
   * We commit the change to version control.
   * We unstash or bring back the original refactor.

The key here is to start at a green state where all the tests pass, shift the code into a more desirable position, verify that we are still green, and carry on with the original work.

Note that it is possible to have multiple Inception Refactorings happening at the same time. Much like the movie Inception, having too many layers can get overwhelming, so try to stick to one Inception Refactor at a time.

This refactor technique is inspired by the [Mikado Method](https://www.amazon.com/Mikado-Method-Ola-Ellnestam/dp/1617291218), a way to sequence incremental refactors by systematically and quickly identifying what will break with a change and then building a grapth of all the necessary changes.

