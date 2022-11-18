---
layout: post
title: "Improving code readability -- turning comments into methods"
date: 2013-02-19 21:49
comments: false
categories: [Code Readability, Craft of Software]           
alias: [/journal/2013/2/19/improving-code-readability-turning-comments-into-methods.html]
---
                 
I'm working with 21 developers to improve their code readability. Through a code read-through, they listen to another developer try and read their code. (See [Code Readability Process]("http://sedano.org/journal/2011/3/30/code-readability-process.html") for more details.)

In reviewing one programmer's code, a sixty line method had a visual rhythm to it. There would be a blank space, a comment, then about ten lines of code, and the cycle would repeat. The comment would explained the code just following it. 

The programmer realizes that the narrative is lost in their code, and feels compelled to add these comments to help the reader understand what is going on. These comments serve as section breaks or chapter headings. 

Instead, the code could be split up into smaller methods, where each method name would clearly revel the intent of the code. The comment would be better served as a method invocation. 

Here's the pattern

```
//determine interest rate  (comment about the code intention)
code
code
code
```


Becomes

```ruby
    determine_interest_rate()
```

Here's the original code

```ruby
    bool Tictactoe::determine_game(int row, int column, char move){
        bool flag = true;
        int i;
    
        // Check the row of latest play
        if(!flag){
           flag = true;
           i=0;
           while((i<dimension) && (flag==true)){
               if(board[row][i] != move){
                   flag = false;
               }
               i++;
           }
        }

        // Check the column of latest play
        if(!flag){
            flag = true;
            i=0;
            while((i<dimension) && (flag==true)){
                if(board[i][column] != move){
                    flag = false;
                }
                i++;
            }
        }
        ...
        return flag;
    }
```

Here's the revised code.

```ruby
	    bool Tictactoe::determine_game(int row, int column, char move){
        bool winner_found;
    
        winner_found = check_row_of_latest_play(row) ||
                       check_column_of_latest_play(column) ||
                       check_...
        
        return winner_found;
    }
```

(Note that I have not shown other refactoring that I would do, as it would distract from the point.)

By changing the comment to a method call, the code is now more "self documenting" and the intent is clear by the method call.

When I suggested this to the programmer, she resisted the idea noting that a method call would affect performance. For a tic-tac-toe problem, this is a specious argument. However, is there merit to it? Will a modern compiler optimize this kind of refactoring? And this brings up a broader question, should we optimize code for performance or readability when we are writing it? Conventional wisdom says we should write code that is clean and easy to understand, and when we are done and have performance analysis with production data, then we know where to spend engineering effort to optimize critical sections. The one exception would be algorithm complexity and running times. (e.g. O(N) vs O(NxN) 

I'm now curious, is this a "comment smell"? Can comments be indicators to us programmers that the code we just wrote isn't very clear. The comment itself my inform us on how we need to refactor the code to make it more readable.
