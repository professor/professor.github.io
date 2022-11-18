---
layout: page
title: "Sustainable Development"
comments: false
categories: [Sustainable Software Development]
sidebar: false 
footer: true 
---

# Sustainable Software Development 
<ul>
  <li><em>combines user centered design with agile software development</em>. Product designers apply design thinking and user research to understand what product and features to build. Extreme Programming relies on an onsite customer to tell the developers what to build. This is problematic in two ways. Often an onsite customer is unavailable, impractical, or too expensive to have on a team. Onsite customers are not trained in design thinking and information architecture.</li>
  <li><em>reduces the commitment level of the team to the work in progress</em>, the stories that each developer is currently working on. Unlike Extreme Programming, the team does not commit to an amount of work to be done during a weekly cycle or iteration. There are no iterations in Sustainable Software Development.</li>
  <li><em>focuses the technical practices on two main goals</em>
      <ol>
         <li>caretaking the code</li>
          <li>removing knowledge silos</li>
      </ol>
      Extreme Programming has many practices around improving code quality, but removing knowledge silos is not an explicit goal.
  </li>
  <li><em>replaces predictions with focusing on "what is the minimal that we need to ship?"</em> Planning Extreme Programming utilizes the team's velocity and backlog to create burn down charts for forecasting the team's progress. Like Extreme Programming, the team maintains a shippable product. 
  <li><em>identifies and removes software development waste</em>. Weekly retros identify wastes and the team removes wastes with action items and chores.   
</ul>

Both Sustainable Software Development and Extreme Programming deal with the tension of dates and features by asking "how do we reduce scope?" and "what should be done first?" In other words, developer happiness and sustainability is achieved by prioritizing the work. 

This table compares Sustainable Software Development to Extreme Programming (XP). 

<b>Balanced Team</b> pulls together various disciplines into one collaborating team. The team works together to accomplish a common goal.
    
##Track One Practices
<b>User research</b> includes writing interview guides (questions), interviewing users and synthesizing the results.
<b>User validation</b> checking whether ideas for the product resonate with users.
<b>Road Mapping</b> the product manager diagrams his or her long term vision for the product.
<b>Story writing</b> literally writing stories that represent potential product features.
<b>Story refining</b> generating small, manageable stories from larger, epic stories.
<b>Project startup</b> a special period of intensive user research and limited coding, typically taking four or more weeks at the beginning of a project or during a major shift in direction.

## Track Two Practices
### Caretaking the Code
<b>Clean code</b> means writing code that is easily understood, easily changed and complies with coding standards the team has adopted. Keeping the code clean requires continuous refactoring. Code craft encourages intention revealing names and discoverable code.
<b>Fast test suite and builds</b> means that the tests execute as quickly as possible. A fast test suite provides speedy feedback to the team when something breaks.
<b>Test Driven Development / BDD</b> has the engineers incrementally build the software by always writing a failing test, then writing just enough code to get that test to pass.
<b>Team code ownership</b> is the ability for any developer on a team to change any of the team’s code.</td>
<b>Continuous refactoring</b>
<b>Integrate frequently</b>
<b>Release frequent frequently</b> means shipping or deploying the product frequently. For a website, “frequent” might mean several times a day; for enterprise software, “frequent” might mean once a month.
Each team releases when features are done or at a given cadence.
<b>Acceptance / staging environment</b> means that the product manager accepts a story in another environment that closely resembles the user’s environment. For installed software, this is another machine or cluster. For web development, this is a staging server.
<b>Build system</b> is for continuous integration or continuous delivery. The build monitor indicates the status of running all the tests with the latest delivered code.
<b>Stop on red builds</b> means that when a build fails (the build monitor turns red), one pair immediately stops what they are doing and fixes the issue. This is not necessarily the pair that caused the build to fail. Shaming whoever introduced the change to cause the build to break is antithetical to the goals of sustainable development. The occasional failing test is not a big deal, the team handles it and moves on.
<b>Knowledge pollination</b> are practices the team uses to push and pull knowledge between team members, often just-in-time.

### Remove Knowledge silos
<b>Continuous pair programming</b> refers to two engineers co-creating source code and tests on pairing workstation with two displays, two keyboards, two mice, and identical development environments. Other models of pair programming exist, but this setup reinforces the equality of the relationship.
<b>Overlapping pair rotations</b> means that, each day, engineers change pairs such that over time, everyone works with everyone else. One member of each pair always retains work in progress from the previous day.

## Boundary Spanning Practices
<b>Backlog grooming</b> the product manager routinely re-sequences the stories in the backlog and verifies that stories at the top of the backlog are ready for engineers to start.
<b>Accepting stories</b> after the team delivers a story, the product manager verifies that the delivered work achieves the acceptance criteria. The product manager tries to break the feature with common unexpected input.
<b>Story showcase meeting</b> a 60 minute weekly meeting to discuss stories that the team will be working on in the immediate future. The product manager describes upcoming stories and the engineers provides feedback on the expected difficulty of each story. The story showcase helps improve the team’s shared understanding of the product.
    
## Project Management Practices
<b>Core work hours</b>
        means the team prioritizes working together in the same office during the same hours. Flexibility with the schedule helps with outside of work constraints provided that the team has enough time in common.
<b>Stand-up</b> is a 5-10 minute, daily meeting where team members discuss changes that affect the team from the previous day’s work and impediments to the current day’s work. If physically possible, people stand to encourage a short check-in. Usually this meeting is at the start of the day, otherwise it is a daily <b>spin-down meeting</b>.
<b>Retro</b>
        a 60 minute weekly meeting in which the team re- flects on the week, celebrates successes, and identifies ways to improve. The ideal retro is a safe environment where a team can discuss any topic constructively.
<b>Flexible scope contracts</b>
    establish an ongoing relationship between a development organization and a client organization without unnecessary details. It might state that the client owns the code, that new releases are expected at most every two weeks, or the daily rate at which engineers are billed. It typically would not state a fixed scope, schedule or budget. If a schedule or budget is fixed, scope is not and vice versa.
<b>No overtime</b>
        means no one is allowed to work overtime except in genuinely exceptional circumstances, such as solving a customer escalation.
<b>Core Work Hours, Be Present</b>
<b>Allocations</b> move engineers where needed. Balance business needs with personal goals.



