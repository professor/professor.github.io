---
layout: post
title: "Sustainable Software Development"
date: 2017-07-14 08:05
comments: false
categories: [Sustainable Software Development]
sidebar: false 
---

There are several ways in which Sustainable Software Development has evolved from Extreme Programming (XP)

Sustainable Software Development 
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

<br/>
<table class=comparison>
  <tr>
    <th>Sustainable Software Development</th>
    <th>Extreme Programming 2.0 (XP 1.0 names)</th>
  </tr>
  <tr class="same">
    <td><b>Balanced Team</b>
    pulls together various disciplines into one collaborating team. The team works together to accomplish a common goal.
      </td>
    <td><b>Whole Team</b> (Balanced Team)
        Whole team is also known as cross-functional teams. Include people on the team with the skills needed for success. Beck points out that a sense of team fulfills an individual’s psychological needs. “We belong. We are in this together. We support each others’ work, growth, and learning.” [1]
    </td>
  </tr>  
  <tr>
    <td>Track One Practices</td>
    <td></td>
  </tr>
  <tr>
    <td class="ident"><b>User research</b>
        includes writing interview guides (questions), interviewing users and synthesizing the results.
    </td>
    <td><b>Real Customer Involvement</b><sup>C</sup> (On-site customer)
        Make the customer a part of the team. “The point of customer involvement is to reduce wasted effort by putting the people with the needs in direct contact with the people who can fill those needs” [1]. Even if a customer is busy, involving them whenever possible is preferred to not involving them at all. In this situation, the team needs to find alternative ways of validating features with users.<br/>    
        It is impractical to have an onsite customer.
    </td>
  </tr>
  <tr>
    <td class="ident"><b>User validation</b>
        checking whether ideas for the product resonate with users.
    </td>
    <td></td>
  </tr>
  <tr>
    <td class="ident"><b>Road Mapping</b>
        the product manager diagrams his or her long term vision for the product.
    </td>Quarterly
    <td><b>Quarterly Cycle</b> (Planning Game, Small Releases)
        Each quarter, the team identifies the stories for the next quarter. During a meeting, the team identifies bottlenecks, initiates repairs, plans the feature sets for the quarter, and selects a quarter’s worth of stories.
    </td>
  </tr>
  <tr>
    <td class="ident"><b>Story writing</b>
        literally writing stories that represent potential product features.
    </td>
    <td><b>Stories</b>
        Stories are “units of customer-visible functionality” [1]. Stories have a name and a description or graphical depiction. Stories track the work to be done.
    </td>
  </tr>
  <tr>
    <td class="ident"><b>Story refining</b>
        generating small, manageable stories from larger, epic stories.
    </td>
    <td></td>
  </tr>
  <tr>
    <td class="ident"><b>Project startup</b>
        a special period of intensive user research and limited coding, typically taking four or more weeks at the beginning of a project or during a major shift in direction.
    </td>
    <td></td>
  </tr>
  <tr>
    <td>Track Two Practices</td>
    <td></td>
  </tr>
  <tr>
    <td class="ident">Caretaking the Code</td>
    <td></td>
  </tr>
  <tr>
    <td class="ident2"><b>Clean code</b>
        means writing code that is easily understood, easily changed and complies with coding standards the team has adopted. Keeping the code clean requires continuous refactoring. Code craft encourages intention revealing names and discoverable code.
    </td>
    <td><b>Code and Tests</b><sup>C</sup>
        The tests and code are the only permanent artifacts. Everything else (e.g. documentation) is generated from the code. Anything that contributes to what the system does today and what it will do tomorrow is valuable, “everything else is waste” [1].    
    </td>
  </tr>
  <tr class="same">
    <td class="ident2"><b>Fast test suite and builds</b>
        means that the tests execute as quickly as possible. A fast test suite provides speedy feedback to the team when something breaks.
    </td>
    <td><b>Ten-minute Build</b>
        Building the code and running the test suite should be automated and short. Longer builds increase the feedback loop.
    </td>
  </tr>
  <tr>
    <td class="ident2"><b>Test Driven Development / BDD</b>
        has the engineers incrementally build the software by always writing a failing test, then writing just enough code to get that test to pass.
    </td>
    <td><b>Test-First Programming</b>
        The developers write tests before writing code. Every production line of code is preceded by a test. Test-first programming addresses several concerns: scope-creep, coupling and cohesion, trust, and rhythm. The practice mitigates against scope-creep; without a clear goal, a programmer can easily write more code than is necessary. The practice improves coupling and cohesion as easy-to-test code often has beneficial design qualities. The practice builds trust in the code as engineers trust tested code more than un-tested code. The practice produces rhythm as it provides a cadence of accomplishing goals.
     </td>
  </tr>
  <tr class="mostly-same">
    <td class="ident2"><b>Team code ownership</b> is the ability for any developer on a team to change any of the team’s code.</td>
    <td><b>Shared Code</b><sup>C</sup> (Collective ownership)
        Everyone on the team can modify any of the system. When engineers sees something broken, they fix it.<br/>
    </td>
  </tr>
  <tr>
    <td class="ident2"> Continuous refactoring</td>
    <td><b>Incremental Design</b> (Simple Design Refactoring)
        Build the system incrementally and evolve the design every day. In the past, software teams might often had long design phases that assumed features would not change. When the team’s understanding of the system changes, make incremental changes to the system to align the code’s design with the team’s desired goal. Teams routinely remove duplication.
   </td>
  </tr>    
  <tr>
    <td class="ident2">Integrate frequently</td>
    <td><b>Continuous Integration</b>
        When working on new features, routinely integrate new code into the master code repository. Avoid long-lived branches. Beck suggests un-integrated code live on its own “no more than a couple of hours” [1]. The longer the team waits to integrate, the more unpredictable and expensive integration becomes.<br/> 
        <b>Single Code Base</b><sup>C</sup>
        Ideally there is only one branch of the code. Multiple branches, (e.g. for releases, or customers) creates extra work. Branches live a few hours at most.
        </td>
  </tr>  
  <tr>
    <td class="ident2"><b>Release frequently</b>
        means shipping or deploying the product frequently. For a website, “frequent” might mean several times a day; for enterprise software, “frequent” might mean once a month.
    <br/>
      Each team releases when features are done or at a given cadence</td>
    <td><b>Daily Deployment</b><sup>C</sup>
        Every day put a new version of the code into production.
    </td>
  </tr>
  <tr>
    <td class="ident2"><b>Acceptance / staging environment</b>
        means that the product manager accepts a story in another environment that closely resembles the user’s environment. For installed software, this is another machine or cluster. For web development, this is a staging server.
    </td>
    <td>(implied)</td>
  </tr>
  <tr>
    <td class="ident2"><b>Build system</b>
        is for continuous integration or continuous delivery. The build monitor indicates the status of running all the tests with the latest delivered code.
    </td>
    <td>(implied)</td>
  </tr>
  <tr>
    <td class="ident2"><b>Stop on red builds</b>
        means that when a build fails (the build monitor turns red), one pair immediately stops what they are doing and fixes the issue. This is not necessarily the pair that caused the build to fail. Shaming whoever introduced the change to cause the build to break is antithetical to the goals of sustainable development. The occasional failing test is not a big deal, the team handles it and moves on.
    </td>
    <td>(implied)</td>
  </tr>
  <tr>
    <td class="ident2"><b>Knowledge pollination</b>
        are practices the team uses to push and pull knowledge between team members, often just-in-time.
    </td>
    <td>(implied)</td>
  </tr>  
  <tr>
    <td class="ident">Remove Knowledge silos</td>
    <td></td>
  </tr>
  <tr class="same">
    <td class="ident2"><b>Continuous pair programming</b>
    refers to two engineers co-creating source code and tests on pairing workstation with two displays, two keyboards, two mice, and identical development environments. Other models of pair programming exist, but this setup reinforces the equality of the relationship.
    </td>
    <td><b>Pair Programming</b>
        Every part of a production system is written by two programmers sitting side by side. The pair works together to solve problems, keep each other on task, learn from each other, and abide by the team’s practices.
    </td>
  </tr>
  <tr>
    <td class="ident2"><b>Overlapping pair rotations</b>
        means that, each day, engineers change pairs such that over time, everyone works with everyone else. One member of each pair always retains work in progress from the previous day.
    </td>
    <td>N/A</td>
  </tr>


  <tr>
    <td>Boundary Spanning Practices</td>
    <td></td>
  </tr>
  <tr>
    <td class="ident"><b>Backlog grooming</b>
        the product manager routinely re-sequences the stories in the backlog and verifies that stories at the top of the backlog are ready for engineers to start.
    </td>
    <td>N/A</td>
  </tr>
  <tr>
    <td class="ident"><b>Accepting stories</b>
        after the team delivers a story, the product manager verifies that the delivered work achieves the acceptance criteria. The product manager tries to break the feature with common unexpected input.
    </td>
    <td>(implied)</td>
  </tr>
  <tr>
    <td class="ident"><b>Story showcase meeting</b>
        a 60 minute weekly meeting to discuss stories that the team will be working on in the immediate future. The product manager describes upcoming stories and the engineers provides feedback on the expected difficulty of each story. The story showcase helps improve the team’s shared understanding of the product.
    </td>
    <td><b>Weekly Cycle (Iteration Planning Meetings)</b>
        Each week, the team accepts a certain amount of work to accomplish. During a meeting at the beginning of the week, the team reviews progress to date, the customer chooses a week’s worth of stories, and the engineers decompose the stories into tasks and individually estimate each task. “The goal is to have deployable software at the end of the week which everyone can celebrate as progress” [1].    
    </td>
  </tr>  


  <tr>
    <td>Project Management Practices</td>
    <td></td>
  </tr>
  <tr>
    <td class="ident"><b>Core work hours</b>
        means the team prioritizes working together in the same office during the same hours. Flexibility with the schedule helps with outside of work constraints provided that the team has enough time in common.
    </td>
    <td>Energized Work (<em>40-hr week)</em></td>
  </tr>
  <tr>
    <td class="ident"><b>Stand-up</b> is a 5-10 minute, daily meeting where team members discuss changes that affect the team from the previous day’s work and impediments to the current day’s work. If physically possible, people stand to encourage a short check-in. Usually this meeting is at the start of the day, otherwise it is a daily <b>spin-down meeting</b>.
    </td>
    <td>Present in http://www.extremeprogramming.org/, but not in the 1999 or 2004 books</td>
  </tr>  
  <tr>
    <td class="ident"><b>Retro</b>
        a 60 minute weekly meeting in which the team re- flects on the week, celebrates successes, and identifies ways to improve. The ideal retro is a safe environment where a team can discuss any topic constructively.
    </td>
    <td>N/A</td>
  </tr>  
  <tr class="same">
    <td class="ident"><b>Flexible scope contracts</b>
    establish an ongoing relationship between a development organization and a client organization without unnecessary details. It might state that the client owns the code, that new releases are expected at most every two weeks, or the daily rate at which engineers are billed. It typically would not state a fixed scope, schedule or budget. If a schedule or budget is fixed, scope is not and vice versa.
    </td>
    <td><b>Negotiated Scope Contract</b><sup>C</sup><
        “Write contracts for software development that fix time, costs, and quality but call for an ongoing negotiation of the precise scope of the system.” [1]
    </td>
  </tr>
  <tr>
    <td class="ident"><b>No overtime</b>
        means no one is allowed to work overtime except in genuinely exceptional circumstances, such as solving a customer escalation.
    </td>
    <td><b>Energized Work</b> (<em>40-hr week)</em>
        “Work only as many hours as you can be productive and only as many hours as you can sustain” [1]. Working longer hours may make the team less productive. Team members need to take care of themselves; this includes staying home to rest when sick. The work patterns of the team should be sustainable in the long run.
    </td>
  </tr>
  <tr>
    <td>
      Core Work Hours, Be Present</td>
    <td><b>Sit Together</b>
        Software development is a collaborative endeavor. Co-locating teams increases collaboration. Distributed teams are still possible, yet “Sit Together predicts that the more face time you have, the more humane and productive the project” [1]
    </td>
  </tr>
  <tr>
    <td>Not needed<br/>
      Agile project management tools (such a Pivotal Tracker)<br/>
      provide more value than a physical board showing project status. 
      </td>
    <td><b>Informative Workspace</b>
        “An interested observer should be able to walk into the team space and get a general idea of how the project is going in fifteen seconds” [1]. The team can modify the workspace to make it more conducive for their work.
    </td>
  </tr>
  <tr>
    <td>Not needed<br/>
        The team does not commit to accompilshing certain stories each week.</td>
    <td><b>Slack</b>
        During the weekly cycle meeting, include tasks in the plan that the team can drop if the team gets behind. Adding slack to the schedule enables a sustainable work environment.
    </td>
  </tr>
  <tr>
    <td>Not needed for all projects</td>
    <td><b>Incremental Deployment</b><sup>C</sup>
        Switch between a legacy system and a replacement system in incremental steps. Avoid a hard switch over from a legacy system to a new system.<br/>
        Slowly replace a legacy systems.</td>
  </tr>
  <tr>
    <td><b>Allocations</b><br/>
        Move engineers where needed. Balance business needs with personal goals.</td>
    <td><b>Shrinking Teams</b><sup>C</sup>
        Try to improve team efficiency so that the team can shrink in size. When a team becomes more productive, re-allocated extraneous team members to other teams.<br/> 
        <b>Team Continuity</b><sup>C</sup>
        “Keep effective teams together” [1]. People are not fungible, and building relationships is part of creating a high performing team. Rotating people through teams helps spread knowledge.
    </td>
  </tr>
  <tr>
    <td>Optional, depends on situation</td>
    <td><b>Root-cause analysis</b><sup>C</sup>
        When a defect occurs, determine why it happened. Modify testing strategy to prevent that kind of mistake from happening again. Write an automated system test and an automated unit test then fix the code.<br/>
    </td>
  </tr>
  <tr>
    <td></td>
    <td><b>Pay-per-use</b><sup>C</sup>
        Pay-per-use provides alignment between revenue and the features that generate the revenue. “Connecting money flow directly to software development provides accurate, timely information with which to drive improvement” [1].
    </td>
  </tr>
</table>

<sup>C</sup> are optional XP 2.0 Corollary Practices

For a team transitioning to Extreme Programming, Beck recommends starting with the primary practices. Beck claims that “the primary practices are useful independent of what else you are doing” resulting in an immediate improvement, whereas the corollary practices work well once a team has implemented the primary practices. Extreme programming is not dogmatic about the list of practices. The team chooses which practices to apply.

Once a team has implemented the primary practices, then the team can start implementing the corollary practices. Beck says that it seems “difficult or dangerous to implement [the corollary practices] before completing the preliminary work of the primary practices” [1].


[1] K. Beck and C. Andres. Extreme Programming Explained: Embrace Change (2nd Edition). Addison-Wesley Professional, 2004.
