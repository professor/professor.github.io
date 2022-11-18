---
layout: post
title: "Theory of Sustainable Software Development through Team Code Ownership"
date: 2016-04-14 20:43
comments: false
categories: [Collaborative Software Development]
---

The theory describes how teams can continue to deliver value in spite of team disruptions. The theory is a collection of synergistic principles, policies, and practices encouraging a positive attitude towards team disruption, knowledge sharing and continuity, as well as caring about code quality. The Theory of Sustainable Software Development through Team Code Ownership is fully presented in the paper.

## Principles
The theory underlying principles are as follows: **Keep a Positive Attitude Toward Team Disruption** by recognizing the value that new team members bring with their fresh perspectives and challenging team assumptions; **Encourage Knowledge Sharing and Continuity** by enabling the knowledge to spread from one developer to the next, eventually reaching the entire team; and **Care about Code Quality** by recognizing that a well cared for code base makes modifications easier.

## Policies
**Team Code Ownership** empowers engineers to modify any part of the system under the team’s responsibility. When engineers agree that a section of the system needs to be changed, the team proactively and tacitly authorizes the change. **Shared Schedule** aligns the team’s work schedule to enable efficient daily rotation of the developers working on a track of feature development. **Avoid Technical Debt** enables a team to balance feature development with Continuous Refactoring. When a team is pressured to finish work by a deadline, it might be tempted to focus on feature delivery, stop refactoring, and hence take on technical debt. The team should prefer consistent software development by caretaking the code and leaving the code base in a state where any member of the team can pick up the next story for that part of the code base. This requires product and management support to avoid unnecessary thrashing of developers rushing incomplete work by taking on technical debt to deliver a feature early.

## Removing Knowledge Silos Practices
By sharing knowledge throughout a team, any pair will have enough context to understand what needs to be done and know who to ask if they need more details. **Continuous Pair Programming** reinforces that there is no single owner for any line of written code. The team owns the code. As two developers collaborate, they generate shared context. That knowledge will spread around the team the following day via **Overlapping Pair Rotation** which explicitly rotates people off a track of work in order to cross-pollinate knowledge and avoid emergent knowledge silos and individual ownership. **Knowledge Pollination** is activities that promote knowledge sharing in unstructured ways between pairs and includes activities such as daily stand-ups, writing on whiteboards, overhearing a conversation, calling out an update to the team, or simply reaching out to others to ask questions as needed.

## Caretaking the Code Practices
By caretaking the code, the team enables any pair to be able to work on any story in the backlog.  **Test Driven Development (TDD) / Behavior Driven Development (BDD)** creates a safety net of tests that give any pair the courage to modify the system without the fear of breaking some other part of the system unexpectedly. The tests become a specification on how each component is used. **Continuous Refactoring** increases code quality by increasing code discoverability (knowing where to find the responsible code), increasing code readability, and increasing the simplicity of design.  **Live on Master** enables the team to perform Continuous Refactoring as the code is easy to integrate. When teams have long running development branches, merge conflicts discourage Continuous Refactoring.

