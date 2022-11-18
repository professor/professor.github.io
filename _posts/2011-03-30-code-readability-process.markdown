---
layout: post
title: "Code Readability Process"
date: 2011-03-30 19:36
comments: false
categories: [Software Engineering, Craft of Software, Code Readability]     
alias: [/journal/2011/3/30/code-readability-process.html]
---
                                                                                                 
## Rationale
As software developers, we want to create clean code, code that is easy for other software developers to read. Ironically, we often don't receive much feedback on our code when we are writing it. Some companies will do code reviews, and the code review feedback may help us write clean code, but we may not understand how other developers are confused. This process allows the programmer to see first hand, what is causing another developer difficulty when they read the code.

## Process
Preparation) There are two roles, a Programmer (someone who has created code) and a Reader (someone who will review provided code). I am an observer of the process.

The Programmer will select recent production code that they have produced. I do not need to see the code and would prefer not to see it. I'd prefer for you to select the most recent code you have created because then you won't be tempted to pick "perfect" or "ideal" code. We're just looking for typical code and presumably whatever you wrote recently is typical. 

I'll prompt the Reader with some open ended questions. The job of the Programmer is to simply receive the feedback. 

Step 1) Programmer, provide some context by explaining the user story (or story card) behind the code. Describe the requirements at a high level in business terms. The Reader should have some notion of the problem the Programmer was trying to solve and the added business value.

Step 2) Reader, read through the code and think out lowd about your initial reaction and your thought process for understanding the code. If things are clear, mention that. If something is confusing, mention the questions that you are thinking. Reason outlowd. There are no wrong answers, this is an opportunity for the Programmer to see how another developer interacts with their code. Provide them with your first impressions.

Do this until you've walked through the code and think you understand it.

Step 3) Programmer, thank the Reader for their invaluable input. Please just say "Thank You" -- there is no need to defend your code

Step 4) Reader, do you see ways to refactor the code? Are there opportunities to make it more dry?

Step 5) Reader, if the Programmer left the company and you had to maintain this code, could you do it?

Step 6) Programmer, are there any clarifying questions that you have for the Reader about their comments? (For example, is there something may be very clear to you, but wasn't clear to the Reader. This is your opportunity to better understand how you could make it more clear.)

Step 7) Programmer, reflect on this experience and describe what was the most useful aspect of it?


Step 8) Programmer, was this worth your time? 


Step 9) Programmer, please fill in the survey response to this exercise


## History

While teaching "the craft of software development" to my masters students, one of my students wanted to write more readable code. I challenged each student to come up with metrics to see if they were improving. The student couldn't think of any. I realized that he would need to show his code to another developer to find out if the code was readable. He could track the feedback as a metric as seen in the comic: http://www.osnews.com/story/19266/WTFs_m
