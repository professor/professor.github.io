---
layout: about
title: "Rework"
author: Todd Sedano, Paul Ralph, Cécile Péraire
footer: true 
---

*The cost of altering delivered work that should have been done correctly but was not.*

Not all rework is waste. Wasteful rework refers to the cost of altering delivered work *that should have been done correctly but was not*. Reworking a product due to unforeseeable or unpredictable circumstances is not waste.

For example, one enterprise team had been shipping Python code while accumulating technical debt over time. The code became so unmanageable that they decided to re-write it in Go from scratch. We see the entire rewrite as rework because ignoring technical debt impairs the understandability and modifiability of software over time, and the team could have avoided the rework by refactoring the original Python code before it became unmanageable.

In contrast, suppose users request a feature and the team builds it. Then, seeing the feature, users realize it is not really what they need and request something quite different. We see reworking the product based on this new information as normal software evolution, not waste, because the team cannot foresee users' changing preferences.

Similarly, refactoring code to handle new features is not waste. A team cannot anticipate and predict future work to be done. Instead, we recommend teams focus on aligning their code with their current understanding of the system features and code design. A team that routinely refractors its code reduces onboarding developer costs and increases its ability to deliver new functionality. Clean code has additional benefits, as clean code is easier to understand, easier to modify, and has fewer defects. Refactoring code to support new functionality is part of the inherent cost of the new functionality. In contrast, rushing a feature introduces "technical debt", which leads to rework and *extraneous cognitive load* (below).

We observed the following causes of "rework" waste:

* Technical debt. This refers to delayed technical work resulting from taking shortcuts in order to save time (often to meet a deadline).

* Ambiguous story definition.This includes ambiguous acceptance criteria and mock-ups.

* Rejected stories. This includes situations where the product manager rejects story implementation because it does not satisfy the acceptance criteria.

* Defects. This includes poor testing strategy and not performing root-cause analysis on defects.

Solutions for avoiding or reducing this waste include:

* Continuous refactoring

* Review acceptance criteria prior to starting a story

* Verify acceptance criteria before finishing a story

* Improving testing strategy and root-cause analysis on bugs

Rework waste is related to a ubiquitous tension between do things well and do things quickly. A recent study of decision-making during programming found that this tension affects many developer actions, including whether to refactor problematic code and whether to implement the first approach that comes to mind or research better ones (Ralph, P. and Tempero, E. 2016. Characteristics of decision-making during coding. Proceedings of the International Conference on Evaluation and Assessment in Software Engineering. ACM.).

For more details, read this [ICSE paper](https://www.researchgate.net/publication/313360479_Software_Development_Waste) or return to the list [software development wastes](index)
