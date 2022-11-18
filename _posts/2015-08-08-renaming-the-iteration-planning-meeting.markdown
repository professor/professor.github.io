---
layout: post
title: "Renaming the Iteration Planning Meeting"
date: 2015-08-08 14:32
comments: false
categories: 
---
# Renaming the Iteration Planning Meeting

## Summary
I suggest renaming the “Iteration” “Planning” Meeting (IPM) to accurately reflect Pivotal’s current goals and practices for that meeting.

## Context
Over time, Pivotal has evolved its own form of Extreme Programming software development methodology by incorporating ideas from Lean Thinking from manufacturing and Lean Startup.

Some of our terminology needs refreshing to reflect the way we currently work. In particular, “Iteration Planning Meeting” does not accurately reflect what typically happens in that meeting.

In [Extreme Programming](http://www.amazon.com/Extreme-Programming-Explained-Embrace-Change/dp/B00CF6EJG8) (1999) and [Extreme Programming 2nd Edition](http://www.amazon.com/Extreme-Programming-Explained-Embrace-Change/dp/0321278658) (2004) the development team commits to the stories to be accomplished during an iteration or weekly cycle just like a sprint in Scrum. The commitment can change as the week unfolds. Once Product identifies the stories for the week, programmers decompose the stories into tasks. After volunteering for a set of tasks, each programmer estimates only their tasks on Monday during an Iteration Planning Game (XP 1999) or Weekly Cycle meeting (XP 2004.) 

In contrast, Pivotal follows a "continuous flow" where the work “flows” through people as people start the next needed story in the backlog. We limit work in progress to a story per pair of programmers. At Pivotal, we’ve customized the Extreme Programming process so that the developers accomplish the work that needs to get done at that moment in time. At any point in time, we can not predict who will be working on what work tomorrow, but we can say who is working on what work now. As that work is finished, we simply start the next unit of work to be done. We do not commit to which stories will be done in any given week, instead we follow a Lean Thinking’s just-in-time mechanisms for identifying what to work on next.

At Pivotal, stories and tasks are not owned by specific individuals. In Scrum and Extreme Programming, one person owns the task for the duration of the task. At Pivotal, many people might work on a single story. While the team notes who is working on each story right now, the team understands that these associations will change. After finishing a task, a development pair simply works on the next available story.

We’re familiar with the multi-day story: On Monday, Bailey and De begin working from the top of the backlog. On Tuesday, De and Kadeer continue on the story. On Wednesday, Kadeer and Lesley finish the story. For the participants, this can feel like a relay race. The entire team might even rotate through a complex story.

Pivotal prefers very small stories in order to deliver value quickly, remove engineering waste, shorten the feature feedback loop, and support iterative and incremental development. The smaller stories often do preclude the need to explicitly list out any tasks. It is rare for a pair of developers to need to list out the tasks associated with a story. Usually, the pair can effortlessly figure out what needs to get done.

We do not follow a Scrum Sprint, or an Extreme Programming Iteration or an Extreme Programming Weekly Cycle. We’ve successfully incorporated Lean into the way we prepare and execute our work.

## The concept of “week” describes the team’s work rhythm
The team’s rhythm aligns with the natural rhythm of a work week. Retros are scheduled on Fridays at the end of the week. The meeting signifies closure for the week. There are practical reasons to schedule the meeting on a Friday. After a weekend off, the team forgets the details of the previous week. Just watch the Monday stand-up for confirmation as team members struggle to recall their stories from Friday. 

The team schedules a “shared understanding” meeting once a week in order to 1) share context from product and design with the engineers. While the engineers are busy implementing stories, product and design are looking into the future work, specifying what needs to be done. This sharing of context helps anyone on the team pick up any story in the backlog. 2) The meeting provides feedback from enginering to product about the complexity and risk of the work. A story that seems simple to product might be expensive to impement. This emergent conversation allows product an opportunity to course correct to a simpler solution.

The meeting typically covers enough stories to make sure that we have enough work in the backlog. Teams typically schedule them on Mondays, Tuesdays, and Wednesdays since any day will do. (This is unlike an Extreme Programming Iteration where these need to be scheduled at the beginning of the week so developers know who is working on what.) If the backlog was extremely full, we could just cancel the meeting. Just because the team’s natural cadence aligns with the week does not mean we are doing Extreme Programming iterations.

The next time you find yourself using the word “iteration”, see if the word “weekly” would do instead. “What is our velocity this iteration?” becomes “What is our velocity this week?” and “How many iterations are left in this project?” becomes “How many weeks are left in this project?” The term iteration is a proxy for measuring time. Since we aren’t committing to work to be done in an iteration, our usage of the terms are interchangeable. 

In communicating our process to potential clients and the outside world, I’d prefer to be accurate in describing our work flow as a Lean just-in-time system. Using the term “iteration” potentially miscommunicates that we are committing to specific work each week.

## Updating our terminology at Pivotal
Since Pivotal has evolved its own form of Extreme Programming to incorporate Lean’s just-in-time practices, I suggest we use the accurate terminology in describing the way we work.

Consider our weekly meeting for creating shared mutual understanding and pointing the next stories in the backlog. Ironically, the meeting is called an “Iteration Planning Meeting” even though we do not commit to which stories we are doing next week and no explicit planning happens in the meeting. While we do point stories in the meeting, examining whether we are on track, re-prioritizing stories, and assigning work to individuals all happen outside the meeting. For us, planning happens at the product manager, client liaison, and client level as Pivotal discusses whether the project is on track and whether key features will be done by a certain date.

During our “Iteration” “Planning” Meeting, it is entirely possible that the stories we do discuss might happen two or even three weeks from now, not during the next “iteration.” 

When I’m anchoring a project, my chief concern with our “Iteration” “Planning” Meeting is to make sure that our backlog has enough pointed stories for the next week. The team running out of work would be disastrous.

Finding a suitable replacement name for this meeting is challenging as many of us have different, sometimes conflicting expectations and goals for the meeting. Here is what I have found n interviewing 10 pivots and product managers from four offices. 

Common goals for the meeting:
1) Create a shared understanding of the work that is to be done.  (Where are we headed? What will we be building? Are we building the right system?) 
2) Communicate to the PM risks and story complexity. We typically use estimation as a forcing function to have this conversation.
3) Estimate the work 
4) Verify that each story has clear acceptance criteria

Goals 1 and 2 are frequently cited in my interviews. Some pivots argue that we should not be pointing and thus goal 3 is not a goal for them in the meeting. Goal 4 is infrequently mentioned.

We could call the meeting a “Pointing Meeting” (PM) which unfortunately has the same abbreviation as Product Manager (PM). In discussing the goals of the meeting with numerous Product Managers, Anchors, and Pivots, I personally prefer the term “Shared Understanding Meeting” as it reinforces the goal of getting everyone on the same page.  

## Updating Pivotal Tracker
Pivotal Tracker might minor updates to its messaging. Pivotal Tracker describes each week as an “iteration” and has charts that talk about “iteration velocity” (aka weekly velocity) “iteration start date” (aka week start date). Fixing this would be a simple string replacement. Fortunately, many of the charts simply reference “Date” instead of “Iterations.” The terminology seeps more into the Help documentation than the tool itself. Keeping the iteration terminology in the help documentation makes sense given that other companies use tracker, and they might have sprints or iterations. Since the weekly markers are not labeled as iterations, one could use tracker for quite some time without knowing that the tool reinforced the Extreme Programming iteration concept from 1999.

## My own A-ha moment
In the movie, the Matrix, Keanu Reaves follows a discovery and evaluation process to determine if he is “The One.” While in a waiting room, he sees a boy bending spoons and wonders how that is possible. The secret is that “there is no spoon.” I had a similar revelation while working on a Pivotal Labs project. In the middle of the work week, I was reflecting on our rhythm of weekly retrospections and weekly pointing meetings and realized that there were no iterations. We did not commit to explicit work each week. Every day felt very much like the next day. We weren’t ramping up on new stories on Monday to wind them down on Friday. Instead, we were present with the features in the backlog. We weren’t planning for or committing to which stories would be done in each week. I mentioned this to my pairing partner and he said, “Of course there are iterations, each Monday we start a new iteration!” The anchor overheard this conversation and said, “Actually, since our project started on a Tuesday, I setup Pivotal Tracker to have iterations go Tuesday to Monday.” With three developers on one team, we had widely different opinions of whether we had iterations and when they started. This conversation reinforced my observation that we were not using iterations as prescribed by Extreme Programming.

## Conclusion
I recommend we replace “Iteration Planning Meeting” with a phrase that accurately describes the meeting’s purpose and goals. I suggest “Shared Understanding Meeting” as a simple draft proposal which is intended to encourage discussion about its disadvantages or the purpose of generating better proposals.

Update 5/10/2017: I now suggest "Story Discussion Meeting" or "Story Estimation Meeting"
