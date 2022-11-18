---
layout: about
title: "Mismanaging the backlog"
author: Todd Sedano, Paul Ralph, Cécile Péraire
footer: true 
---

*The cost of duplicating work, expediting lower value user features, or delaying necessary bug fixes.*

Mismanaging the backlog includes all the waste associated with poor prioritization. One kind of prioritization problem specific to agile software development is *backlog inversion*, which occurs when the team starts working on stories that have not been prioritized recently.  For instance, on Monday, the product manager examines the backlog and re-prioritizes the next seven stories. The team finishes those seven stories and begins working on stories eight, nine and ten. Since these stories have not been prioritized recently, the team might unknowingly be working on low priority stories.

We observed the following causes of "mismanaging the backlog" waste:

* Backlog inversion

* Working on too many features simultaneously

* Duplicated work

* Not enough ready stories

* Imbalance of feature work and bug fixing

* Delaying testing or critical bug fixing

* Capricious thrashing

Duplication of work can happen when individuals and teams are not effectively communicating. For one project---a multi-node database cluster---coordination happened between 15 development teams with 74 software engineers. Over time, they developed 16 different ways to provision a cluster using scripts, docker, custom tools, bosh, and terraform. Developing a single comprehensive solution would have taken one team slightly more time but save substantial resources overall.

At Pivotal, product managers typically write the user stories. We observed engineers sometimes resorting to writing stories instead of the product manager. This happened when the backlog was empty or when they knew something needed to be done, but no corresponding story had been written. Here, engineers writing stories often indicated prioritization problems, or the product manager not staying far enough ahead of development.

Solutions for avoiding or reducing this waste include:

* Prioritizing the backlog several times a week

* Minimizing work in progress by finishing features before starting new ones

* Updating the backlog with current work in progress

* Writing enough stories to stay ahead of development

* Routinely working on bug fixes while doing feature development

* Receiving feedback from users before making changes

This waste is also related a tension: **intransigence versus capricious trashing**. Responding to change quickly is a core tenet of agile development and often thought of as the opposite of refusing to change. However, responding to change is more like a middle ground between intransigence (unreasonably refusing to change) and thrashing (changing features too often, especially arbitrarily alternating between equally good alternatives). As an example of trashing, on one project, the launch was delayed while the business fiddled with the sequence and number of steps in the user registration process.

For more details, read this [ICSE paper](https://www.researchgate.net/publication/313360479_Software_Development_Waste) or return to the list [software development wastes](index)
