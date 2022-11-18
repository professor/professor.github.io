---
layout: about
title: "Extraneous cognitive load"
author: Todd Sedano, Paul Ralph, Cécile Péraire
footer: true 
---
 
*The costs of unnecessary mental effort.*

Human beings have limited working memory and mental resources. Technically, cognitive load refers to how much working memory a task requires. Here, however, we are using extraneous cognitive load more generally to mean the costs of making something unnecessarily mentally taxing.

For example, one project used five separate test suites that each worked differently. Running the tests, detecting failures, and rerunning just a failed test required learning each tool. This was unnecessarily cognitively taxing in two senses: 1) developers had to learn the five systems initially; 2) developers had to remember how all five systems worked and avoid confusing them.

We observed the following causes of "extraneous cognitive load" waste:

* Technical debt

* Complex or large stories

* Inefficient tools and problematic APIs, libraries, and frameworks

* Unnecessary context switching

* Inefficient development flow

* Poorly organized code

Solutions for avoiding or reducing this waste include:

* Refactor code that is difficult to understand

* Decompose large and/or complex stories into smaller and/or simpler stories

* Replace hard to use libraries

* Work on one task at a time until it is completed; avoid "blocking" tasks (i.e. putting a task on hold to work on something else)

* Improve the development flow including better scripts and tools

For more details, read this [ICSE paper](https://www.researchgate.net/publication/313360479_Software_Development_Waste) or return to the list [software development wastes](index)
