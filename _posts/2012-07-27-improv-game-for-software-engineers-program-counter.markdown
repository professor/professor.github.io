---
layout: post
title: "Improv game for software engineers: Program Counter"
date: 2012-07-27 14:06
comments: false
categories:  Improv       
alias: [/journal/2012/7/27/improv-game-for-software-engineers-program-counter.html]
---

I invited this improv game themed around software development for some Brazilian computer science students visiting my campus. It's a variant of the many reaction based, warm-up games (e.g. "Whoosh Ball") that encourage quick response time and discourages over-thinking or planning a response. I like playing it with software developers because it makes more sense to them than these other games.

### Instructions
Have the group form a circle. 

Explain that we are going to mimic a program counter moving around the circle. Each person gets to say the instruction that the program counter is going to do. The instructions are **"Op"**, **"Loop N"**, **"Method Call"**, **"If true"**, **"If false"**

**"Op"** -- There are a variety of operations that a normal CPU would do, such as add, subtract, store to a register. For this game, we'll simplify all of these possible operations into a single command "op" -- have the entire circle practice that command going around. Pretty simple. Let's make it more interesting.

**"Loop N"** -- A basic control flow of most programming languages is the ability to go through a loop and do multiple instructions each time. If someone says "loop 3" this indicates that we are iterating over a collection with three elements. The next person says "one" indicating that the first set of instructions is now happening. The next person says "two". The next person says "three". Then we proceed as normal. (I've seen one group say "Loop Zero" which we treated as a finished loop. It's just like saying "Op") We do this for awhile until people get it.

**"Method Call"** and point to someone or say their name out loud -- Often programs re-use code by calling a method on that section of the code. If someone says method call and points to someone we are jumping to that section of the code. (That person needs to decide which way the program counter will continue.)  We keep executing instructions until someone says **"return"** at which point the program counter goes back to the person who said "method call" (Sometimes people will think that it returns to the person who was pointed at, but it returns to the person who started the method call, just like a real program.) Yes, method calls can be nested multiple times and even have recursion. 

I personally like this operation. In many improv games, the equivalent operation is often a chance for the person to pass control to someone else without cost. E.g. I panic, I don't want this thing, I think it's a "hot potato" so I'm going to give it to you quickly by saying "Zoom" so that I don't have to deal with it. However, in this game, there is a cost of saying "Method Call" for the person, they have to remember that they said it. Everyone else in the room, just really needs to track the depth or number of method calls that have been said, where as the people who say method call need to remember where they are on the stack. 

**"If true"** and **"if false"** -- eventually we get tired of going around in the same direction -- Our program counter is pretty simple and can't deal with branch predictions so whenever we use the IF statement, we pay a performance penalty and skip the next step, e.g. the next person. "If true" then will skip the next person. "If false" then reverses the direction and skips the next person. (Here's an example, if we moving clockwise and you say "if true", we skip the person to the left. If you say "if false", it skips the person to the right and proceed clockwise.) 

**"Cheer"** -- As soon as the first mistake happens, agree upon a verbal saying that symbolizes, "We are having fun, we made a mistake, and we get to restart!" In my improv training that's been "Ah-ooo-ga", the Brazilian students preferred "Ciao!" and I've seen other positive vocalizations.

### Other considerations
After introducing these instructions, I allow the group to invite any programming constructs that they can think of, and I say "yes" to any suggestion no how bizarre it is. Sometimes I'll allow the group to tweak it if it isn't clear. If you try something let me know.

One variant of "**op**" is to allow them to create any normal single instruction operation. They could say "add", "store", "multiply" instead of "op" -- I suspect that doing this might be best at the beginning, but I have not tried that experiment.

Feel free to use this game. I'm assuming that no-one will ever remember that I invited it. =)

### Game History
On February 20, 2012, a student group from [Uniasselvi University](http://www.uniasselvi.com.br)
in Brazil visited Carnegie Mellon University in Silicon Valley. Since I don't know Portuguese, Professor Jan Charles Gross graciously translated my instructions. 

<span class="full-image-block ssNonEditable"><span><img src="/images/ToddSedano%20with%20JanCharlesGross.png" alt=""/></span></span>

Professor Gross' son, Professor Sedano, Chris Zeise, Professor Gross
