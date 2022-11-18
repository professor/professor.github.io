---
layout: about
title: "Unnecessarily complicated or complex solutions"
author: Todd Sedano, Paul Ralph, Cécile Péraire
footer: true 
---

*The cost of creating a more complicated solution than necessary, a missed opportunity to simplify features, user interface, or code.*

Unnecessary complexity is intrinsically wasteful and harmful (Maeda, J. 2006. The Laws of Simplicity. MIT Press.). The more complicated a system is, the more difficult it is to learn, use, maintain, extend and debug.

Unnecessary feature complexity wastes users' time as they struggle to understand how to use the system and achieve their objectives. For instance, one product required the user to fill in form fields not related to the task at hand. Implementing these unnecessary fields also wasted development's time by making the technical solution overly complex.

We observed the following causes of "unnecessarily complex solutions" waste:

* Unnecessary feature complexity from the user's perspective. This includes overly complex user interactions and business processes.

* Unnecessary technical complexity from the team's perspective. This includes duplicating code, lack of interaction design reuse, and overly complex technical design.

Solutions for avoiding or reducing this waste include:

* Prefer simple designs for user interaction

* Prefer simple designs for software code

We observed the following tension in relation to this waste: **big design up-front versus incremental design**. Up-front designs can be based on incorrect or out-of-date assumptions, leading to expensive rework especially in rapidly changing circumstances. However, rushing into implementation can produce ineffective emergent designs, also leading to rework. Despite the emphasis on responsiveness in agile development, designers struggle to backtrack on important decisions and features (Cross, N. 2001. Design cognition: results from protocol and other empirical studies of design activity. Design knowing and learning: Cognition in design education. C. Eastman, W.C. Newstetter, and M. McCracken, eds. Elsevier Science. 79–103.)

The logic of avoiding rework underlies disagreement over big design up-front versus incremental design—proponents of both approaches feel that they are reducing rework. However, on the observed projects, no amount of up-front consideration appears sufficient to predict user feedback and product direction. Therefore the observed teams preferred to incrementally deliver functionality and delay integrating with technologies until a feature required it.

For more details, read this [ICSE paper](https://www.researchgate.net/publication/313360479_Software_Development_Waste) or return to the list [software development wastes](index)
