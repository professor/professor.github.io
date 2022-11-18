---
layout: post
title: "The Origins of Collaborative Software Development"
date: 2016-01-30 15:31
comments: false
categories: [Collaborative Software Development]
---

Collaborative Software Development is the combination of practices from Extreme Programming, Kanban software development, User centered design, and Lean Start-up.

Kent Beck's Extreme Programming serves as the bedrock foundation for the practices at Pivotal. The company through Rob Mee experimented and piloted these ideas which formed the DNA for our software development practices. Over time these evolved. 1) The core technical practices remain the same. 2) Managing the backlog evolved from managing commitments for an iteration to just in time scheduling of work. By creating small stories, the need for story to task decomposition disappeared. Iteration planning meeting morphed into bi-directional communication about the immediate work to be done in order to create a shared context for the whole team. This removes unnecessary team task breakdown waste, mid-week checking in on programmers waste. It enables product to change the backlog whenever necessary by shifting stability from the iteration to the story. It enables developers to be present with the work and not focused into the future.  3) While Extreme Programming shifted the definition of features from engineers to product, XP did not specify how product determines these features (See below for more details.) XP enabled the developers to focus on the how and product to focus on the what.

When I first learned about Extreme Programming, it was described to me as "cowboy programming" and an excuse for developers to run amok with little discipline. I have been programming and teaching it since 2005 and can currently cannot imagine a saner way of developing software. I find it incredibly disciplined, applicable to many contexts, and I rely more heavily on it for challenging projects.

Collaborative Software Development's programming in the present comes from Kanban software's idea of no iterations. The team looks to design and product to periodically communicate and discuss the next bit of work to be done. Typically this happens weekly or more frequently. Since the team is not focused on a fixed amount of work for a period of time,
changes in priority do not necessarily interrupt team productivity. If design discovers a problem with a user interaction, a story to fix the issue can be added into the backlog and prioritized as the next most important thing to be done. Problems can arise if the team has no context on the work to be done, and performing an impromptu shared understanding meeting alleviates this problem. If too much trashing happens, the team needs to understand why there are daily fluxes in prioritization.

When I first heard about no iterations, I thought the idea was crazy. However, having experienced it myself, I appreciate the ability to show up at work and see what is the next important thing to get done.

Collaborative Software Development's validation of features by users comes from user-centered design and popularized by Lean Startup. The approach prioritizes the user's needs over perceived business desires and suggests that conflicts between the two should result in examining the business desires in order to align with what the consumer wants. This idea also comes from Lean Thinking which defines delivering only what the user wants as value and delivering anything that the user does not want as waste.

Lean Software Development is not a direct influence on Collaborative Software Development. Several of the ideas of lean thinking for reducing do show up. (Co-located teams, short feedback loops, anyone can stop software development by starting a team huddle.) Just as it is problematic to apply construction practices to software development, so to it is to apply manufacturing practices to software development. In Lean Thinking, most of the attention is on optimizing the production of identical components on an assembly line, not discussing how to optimize the design process of creating new products. While some software products are simply configured, at Pivotal, most it is rare for us to build the same component over and over again. Whenever that occurs, we design it once or refactor the code so that adding more is a trivial exercise. Since the work that we do is not repetitive like an assembly line, applying manufacturing technics to software development can be problematic.


