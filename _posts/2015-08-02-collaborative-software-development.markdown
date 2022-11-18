---
layout: post
title: "Collaborative Software Development"
date: 2015-08-02 15:31
comments: false
categories: [Collaborative Software Development]
---

I’m still editing this blog post and it is subject to change. While what I want to say isn’t changing, the words that I use to say it are changing.

# Collaborative Software Development
Collaborative Software Development is an evolution of Extreme Programming method with iteration-less development. Collaborative Software Development starts with all of the practices of Extreme Programming (XP) and replaces the concept of iterations with Lean Thinking’s just-in-time production philosophy manifested in pulled-based practices. This achieves a high quality, extremely readable, and well designed software with a faster ability to respond to change.

Collaborative Software Development continues to rely on all the technical practices of XP including pair-programming, test-driven development as well as the remaining process practices of XP including on-site customer.

# Commitment level shifts from the iteration to story
While there is a commitment to the story in-flight, the developers with the product manager may realize that the story needs changing. While working on a story, the developers might discover a corner case not considered by the product manager, or find a confusing user interaction flow that requires the user experience to be re-worked. For these emergent and “internal” changes, the story needs updating. (reduces the waste from more design-up-front approaches. This is an advantage of the process.) For “external” changes where the product owner changes the feature, typically the product owner creates a new story that reflects the new insight into the feature. From this perspective, there is a commitment between the product owner and the team that the stories written reflect our current understanding of the system and will not be re-written by product.

By switching from an iteration based to a just-in-time workflow, the commitment level changes from the iteration to the story.  In Extreme Programming, there is a weekly contract between the product owner and the development team that the work for a particular week is fixed. Anything can change about the project, as long as the changes occurred between iterations. With Collaborative Software Development, the product owner is committing to the completion of any story in flight since it was at the top of the backlog when available developers pick it up and start working on it. In practice, product owners do not cancel in-flight stories. Stories might become blocked and be un-started. Theoretically it is possible that the direction of a project changes so drastically that you might stop working on a story, but in practice this is extremely rare. 

# Being in the moment
In this environment, developers learn to be flexible when showing up at work, just like actors performing improvisation without a script. Imagine a developer with expectations about their work for the day. At the beginning of the day, they pair up, and the pair may discover that the team’s needs will cause the developer’s expectations to be misaligned from reality. Developers learn to loosely hold any expectations and embrace what emerges in the day. Developers can be pleasantly surprised by what emerges. “Acceptance is the answer” to many of life’s problems. A developer can express their desires to the team. Examples include “I haven’t worked on this part of the code base recently” or “I haven’t paired with this person in awhile” or “I really enjoy working on UI stories.” However, if the build is broken, or the product manager needs help in accepting a story, then the reality of the moment will trump any of the developer’s plans.

Improvisors practice letting go of planning through exercises that reinforce handling of chaotic situations, rewarding spontaneity, and listening. In Lean XP, we learn to listen to our pairs, our tests, our code, our stories, our product owner, and our users. 

“You Aren’t Going to Need It” (YAGNI) encapsulates part of this idea. Instead of worrying about future features, let’s focus on the current system and implementing the current feature. At its heart, its about being in the present with the code. By not committing to stories for each week, it shifts the conversation. Instead of discussing what was done last week, or what will be done next week, the team can focus on what needs to be done now. 

# Pros
**This approach encourages flexibility in the developers.** I don’t know what I’m working on today. If I do have plans, I need to be willing to let go.

**This approach allows for quick re-distribution of the work.** As developers finish a story, they will pick up the next important one. The PM can re-prioritize the backlog at any point and know that the most important story will be worked on as soon as a pair finishes their current work. 

If everyone was committed to a task within a sprint, then explicitly coordination is required to determine which tasks should be postponed and dropped. Dependencies on those tasks could also be affected.

**This simplifies the plan of work for the week** Some engineering managers maintain intricate mappings of who is working on what and who is dependent upon what. If any one developer slips on their work, there is other work that is also delayed. Lean XP shifts the focus from developer dependency to story dependency. Stories that block other stories can be explicitly labeled. When the first story finishes, the second story can be unblocked and worked upon when it reaches the top of its backlog. There is no “chess” game of resource allocation and dependency management.


How is a SE kanban board lean? Instead of tracking about all of the requirements of a product, we can just track the stories in the next iteration or the features in the next release?


