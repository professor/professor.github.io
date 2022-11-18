---
layout: post
title: "TDD: small Ah-Ha moment on when to use a hash instead of an array"
date: 2012-07-20 13:34
comments: false
categories: [Craft of Software]                                   
alias: [/journal/2012/7/20/tdd-small-ah-ha-moment-on-when-to-use-a-hash-instead-of-an-a.html]
---
                                               
I'm sharing a pleasant surprise I had during a recent Test Driven Development coding session. My tests had found a design that was delightful to me. TDD suggested that I use a hash where my natural tendency is to use an array. 

For the purpose of clarity, I'm simplifying a very complicated data structure for this example. Let's say we wanted to show the user the most popular cheat codes for a set of video games. For the sake of the example, let's assume that this information is stored in the database in a way that is rather difficult to access. Thus the need for a method "most_popular_cheats" to do the heavy lifting. 

Let's recall some popular cheat codes. Contra's cheat code is "UP, UP, DOWN, DOWN, LEFT, RIGHT, LEFT, RIGHT, B, A, START"  and Mike Tyson's cheat code is "007-373-5963"

From the control flow, I would already know the order of the video games that needed cheat codes, and expected that the method "most_popular_cheats" would just return an array.

However, as I wrote the test first, I realized that the test wouldn't know the exact order of the video games. After I created some test data in the database, I wasn't certain how they would be retrieved, would the default sorting be by ID, or by name? The test didn't know and I didn't think the test should care. If the method returned a hash, I could just see if the hash contained the key->value pairs that I expected.

    Hash: {contra.id => "UP, UP….", mike_tyson.id => "007-373-6963"}

On previous projects, following the traditional "code then test" development style, I have generated two parallel arrays to solve this problem kind of problem. One that contained the answer (what is my value in my hash), and the other that contained the index (what is my key in my hash.) On those projects, it had not occurred to me that a hash was a better data structure. My tests informed me on a programming nuance that I had previously missed.

Here's the simplified version of test case that lead me to this small ah-ha moment.

    contra = FactoryGirl.create(:video_game_with_popular_cheats)
    mike_tyson = FactoryGirl.create(:video_game_with_popular_cheats)

    popular_game_cheats = Game.most_popular_cheats
    popular_game_cheats = should be_a_kind_of(Hash)
    popular_game_cheats[contra.id].should = "UP, UP, DOWN, DOWN, LEFT, RIGHT, LEFT, RIGHT, B, A, START"
    popular_game_cheats[mike_tyson.id].should = "007-373-5963"
