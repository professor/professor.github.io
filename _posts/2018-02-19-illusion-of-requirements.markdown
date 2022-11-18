---
layout: post
title: "Illusion of Requirements"
date: 2018-02-19 07:58
comments: false
categories: 
---

# The Illusion of Requirements; the Requirements Myth

"Requirements" is a pre-agile construct based on our false belief that building software was somehow like the construction of buildings.

"Requirements" limits the development team into thinking the end product is fixed and that the team's goal is to implement a specification.

Agile development teams expect features to change over time. Even with thorough user research and validation, the product will change as soon as we receive user feedback. Even during the implementation of a user story, an emergent conversation on the team might change its acceptance criteria.

In contrast, features are a construct of preferences. Many preferences may stay the same, some will change over time, and most are made up on the spot [Lichtenstein and Slovic 2006](http://www.cambridge.org/id/academic/subjects/psychology/cognition/construction-preference).

## A simple example
Let’s consider a simple and common feature request: "the user logs into the system with a username and password." If we consider this request to be fixed, we might not consider alternative solutions.

   * Some websites support magic links. You don’t type in a password, the system emails you an authentication link. 
   * Some websites require two-factor authentication.
   * Some websites rely on a third-party single sign-on such as Google, Facebook, or Okta.

Several of these solutions also attempt to solve the problem of users creating easy to guess or easy to break passwords. 

Treating authentication as a "requirement" misses these opportunities.

## System characteristics
How then do we deal with performance, scalability, availability, recoverability?

Pre-agile has the notion of "non-functional requirements" which describe system characteristics or product quality characteristics.

### Performance
Before agile, I wrote my share of statements like "the web page should load in under 0.5 seconds." In reflection, my non-functional "requirements" were arbitrary limitations on the system. 

Here's the typical workflow for agile software development.
   * Conduct user research and validation to determine appropriate feature for the opportunity
   * Build a minimal implementation of the feature
   * Verify that the feature matches the opportunity, if not iterate
   * Improve performance where needed
This is a variant of "Make it work, make it right, make it fast."(http://wiki.c2.com/?PrematureOptimization)

### Availability and Recoverability
Many of the system characteristics such as availability can influence Service Level Agreements. Pre-agile treats these as guarantees. If we build the system just right, we can guarantee that we will achieve a particular outcome. Agile treats these as goals. If we want to prove ourselves that the system handles disruptions, then we introduce disruptions much like Netflix Chaos Monkey. We keep iterating on the product and deployment process until we achieve the goal. Adding Chaos Monkey to a system could be considered a "non-functional story" or a chore, since it provides no user facing functionality yet improves the product's quality.

## Avoid pre-agile constructs
It can be hard to remove bias from pre-agile constructs. If you see yourself or your team using the following words, pause and reconsider your options: 
   * specifications, 
   * requirements, 
   * the system shall...

## In Summary
Avoid limiting yourself with pre-agile concepts. Recognize the flexibility of features in building software. 


Here's an [academic paper](https://www.researchgate.net/publication/265416695_Requirements_Fixation) demonstrating the negative impacts of framing potential system functionality as "requirements."   

For more information about the construction of preferences see http://www.cambridge.org/id/academic/subjects/psychology/cognition/construction-preference
