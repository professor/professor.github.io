---
layout: about
title: "Waiting / multitasking"
author: Todd Sedano, Paul Ralph, Cécile Péraire
footer: true 
---

*The cost of idle time, often hidden by multi-tasking.*

When something goes wrong in a manufacturing plant, we can sometimes see people waiting around. If the boxing team runs out of boxes, they might just stand idle until more boxes arrive. This is obviously waste.

Waiting waste is less obvious among software professionals because waiting is often hidden by multitasking. For example, if the integration process takes an hour, programmers tend to switch to some other, lower priority work while waiting for integration.

Multitasking introduces waste in two ways. First, multitasking involves a mental transition to the new task, which can be quite time-consuming, especially if the new task is cognitively demanding. Second, multitasking creates dilemmas when the original high-priority task becomes available again. Do developers finish the second lower-priority task (delaying higher priority work) or immediately switch back to the original task (leaving work-in-progress)?

We observed the following causes of "waiting/multitasking" waste:

* Slow, flaky, or unreliable tests

* Missing information, people, or equipment

* Product manager taking a long time to respond for needed information

* Context switching between tasks

Related to this waste, we observed a common tension: **waiting versus context switching**. This tension comes from having to choose between two evils. Indeed, having engineers remaining idle for more than a few minutes is not acceptable (at least in the western software development cultures with which we are familiar). Consequently, engineers tend to favour context-switching over waiting despite the drawbacks described above.

For short waits, we observed engineers take breaks (e.g. play table tennis). For longer waits, we observed engineers use waiting time to attempt to remedy problems or reduce the duration of future waiting (e.g. shorten the build). When this was not possible however, engineers resorted to task switching, often with the effect of hiding the waiting waste.

To reduce this waste, it helps to first exposing the waiting time by, for example, limiting work in progress to reduce task switching. Engineers can use waiting time to improve the situation by, for instance, figuring out how to speed up a long build.

For more details, read this [ICSE paper](https://www.researchgate.net/publication/313360479_Software_Development_Waste) or return to the list [software development wastes](index)
