---
layout: post

title: "Considerate Pair Programming - Part 1"

date: 2017-10-24 08:37

comments: false

categories: [Pair programming]
---

## Why We Pair

Hi. I have come to love Pair Programming. I enjoy the collaboration, cross-training, and better solutions that emerge while I pair.

Continuous Pair programming with Overlapping Pair Rotations removes knowledge silos to increase teams' resiliency to team disruption [[reference](https://www.researchgate.net/publication/304014117_Sustainable_Software_Development_through_Overlapping_Pair_Rotation?ev=prf_high)]  and builds collective code ownership [[reference](https://www.researchgate.net/publication/301612260_Practice_and_Perception_of_Team_Code_Ownership?ev=prf_high)] as described in Sustainable Software Development.

Pair programming is a complex practice requiring skill to master. Although Pair Programming has been around for 20 years and is well researched, some teams simply drop engineers onto a team expecting them to figure Pair Programming out. 

As a practitioner, I am still discovering ways that I can improve the pair programming dynamic. 

This article describes 1) several techniques that can improve your pair programming experience, 2) strategies on what to do when things get frustrating or go wrong, and 3) concludes with success stories of converting difficult pair-programming relationships into successful pair-programming relationships. 

Like any relationship, such as friendships, family dynamics, dating, or marriage, when pairing works well, it is an amazing experience; when pairing falls apart, it can be frustrating and occasionally super hurtful. While unfortunate dynamics can happen while pairing, I have experienced the joy of finding each other in the rift.

Pairing exposes both our strengths and our weakness. How we handle our weaknesses may have a direct impact on the pairing relationship. One of us might not be comfortable exposing our weaknesses. If we are experiencing imposter syndrome, feeling that we are not qualified for the job we have, we might fear that our partner is going to find out that we are faking it.

I have been on a journey to be a better pair. While at Pivotal over 3.5 years, I have paired with ~39 pivots and ~ 20 client developers. I am grateful to each person who has helped me better understand myself and have helped me assemble and create these techniques. If you paired with me and I did not apply the technique, it may be because I learned it later.

<!-- more -->

This is Part One in a three part series covering strategies, techniques, and tips for Considerate Pair Programming.

[Part One](http://sedano.org/toddsedano/2017/10/24/considerate-pair-programming.html) covers *Why We Pair* and *Setting up the Work Environment* for success.

[Part Two](http://sedano.org/toddsedano/2017/10/23/considerate-pair-programming.html) covers *Strategies for Success* including 

* welcoming interactions at different parts of the day, 

* reflecting on the pair programming experience, and 

* reframing interactions for growing collaboration.

[Part Three](http://sedano.org/toddsedano/2017/10/22/considerate-pair-programming.html) covers what to do *When Things Go Weird*

Remote pairing presents its own set of challenges. See [my remote pairing blog post](http://sedano.org/toddsedano/2016/11/07/remote-pair-programming.html) for techniques to improve remote pairing effectiveness.

*Our overarching goal is to create a welcoming and safe environment for both pairs.*

Here are playing cards that cover these techniques: <br/> <a target="_blank"  href="https://www.amazon.com/gp/search/ref=as_li_qf_sp_sr_il?ie=UTF8&tag=sedano-20&keywords=B07L8QF3RC&index=aps&camp=1789&creative=9325&linkCode=ur2&linkId=b2796fa6fc83c70a8bdcc703f59a801e"><img border="0" src="//ws-na.amazon-adsystem.com/widgets/q?_encoding=UTF8&MarketPlace=US&ASIN=B07L8QF3RC&ServiceVersion=20070822&ID=AsinImage&WS=1&Format=_SL250_&tag=sedano-20" ></a><img src="//ir-na.amazon-adsystem.com/e/ir?t=sedano-20&l=ur2&o=1&camp=1789" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

## Setting up the Work Environment

**The computer**

What: Configure the work environment to make pair programming effective. Set up a pairing workstation with two monitors, two keyboards, two mice, and one computer. Make sure there is ample room for two people to work side by side at one desk. Ideally, all the team's machines are similar in configuration enabling frictionless pair rotations. Pivotal uses [workstation-setup](https://github.com/pivotal/workstation-setup) when adding new machines to a team to provide a consistent experience with common tools. 

Why: a welcoming environment that enables both pairs to work efficiently improves productivity.

Anti-pattern: Avoid using individual laptops for pair programming. After seven projects using pairing workstations, I joined a team that used laptops with external monitors for pairing. The team did not view laptops as communal team property. Each person configured their laptop differently suiting their personal development process. One pair ignored my feedback about the development environment.  At the time, I felt like an unwelcomed guest in someone else's home. 

**The physical environment**

What: Create a conducive work environment that treats each person as an equal.

Why: Small physical differences can create power imbalances. 

Example: On one project, we had a window seat. We intentionally rotated everyone through the more desirable location.

Example of simultaneously standing and sitting: On one project we used varidesks to allow each person to be able to stand or sit whenever they felt like it. Often I would mirror my partner. If they stood, I stood. If they sat, I sat. At some point, I broke away from this rhythm. Initially, the status dynamic felt unequal whenever one of us stood and the other sat. After acknowledging the differences, and practicing it both ways, I am now ok with the dynamic. However, when beginning new pairing relationships, I would prefer to describe my experience and check-in with my pair before creating a potential power imbalance. 

<span class="thumbnail-image-block ssNonEditable"><span><img src="/images/bad-pairing-setup-depth.jpg" alt="Developer pair programming"/></span></span>

Imbalance in desk depth.

Anti-pattern: For one project, the table did not have a straight edge. One side of the table had more depth and the other side was shallower.  The difference was 15 centimeters (6 inches). The side with more desk spaces felt like the dominant side, whereas the side with less desk space felt less important and inferior. Possible solutions include changing team space or buying replacement desk pieces for that cubicle vendor.

<span class="thumbnail-image-block ssNonEditable"><span><img src="/images/bad-pairing-setup-width.jpg" alt="Developer pair programming"/></span></span>

Imbalance in sharing space. 

Anti-pattern: I saw two people pairing in this space. The person on the left has ⅓ of the space. The person on the right has ⅔ of the space. Interestingly, the desk's seam is exactly between the two monitors which may explain this odd configuration. 

(I only saw these two people in this space for one day. They were visitors to the building and had planned to talk to one of them the next time I saw them. If I had a do-over, I would like to have raised this issue with them.)

Here’s an example which equalizes the physical environment. It does not matter which side you pick for the day. <span class="thumbnail-image-block ssNonEditable"><span><img src="/images/good-pairing-setup.jpg" alt="Developer pair programming"/></span></span>

Thank you to John Ryan and Ian Ornstein for their feedback on this series. 

## Summary

We want to create a space that is welcoming for pair programming and treats each person as an equal. 

I started experimenting and developing these techniques when I suffered through some difficult pair programming experience. If you have had a challenging experience, I would like to hear what it was like for you and how you went about solving it. Email me at professor@gmail.com 

You might enjoy the [book](http://sedano.org/book) I'm working on. The book describes how Pivotal leverages pair programming and several other practices so that its teams can survive major disruptions.
<a href="http://sedano.org/book"><img border="0" src="/images/book3.png" alt="Brady Bunch View"/></a>

<sup>Sustainable Software Development: Extreme Programming Evolved &trade;</sup>
