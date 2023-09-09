---
layout: post
title: Boolean workshop
date: '2023-07-14'
categories: Workshop
tags: NOAA Rclub workshop if else boolean
---

# If / Else Workshop

## Click 'Visual' at the top of this window for the formatted experience

'if else' statements are a simple yet powerful tool that can demystify the 'ones and zeros' of coding. If you can logically reach your desired outcome from a series of true and false statement, you can do anything!

**OBJECTIVE:**

-   use conditional statements to control large data sets, converting values based on conditional criteria

    -   a custom tutorial is provided to become familiar with if else statements!

    -   a few questions for group work

-   familiarize ourselves with common logical operators

    -   `!` = NOT

    -   `&` = AND (element wise)

    -   `|` = OR (element wise)

## Intro to boolean variables

-   boolean (computing definition) - a binary variable or outcome as 'true' or 'false'

**Conditional statements -** if else statements following a boolean logic, meaning a series of binary true and false outcomes. They are are coded in R as the following:

**if** ( statement here ) {

outcome if true

} **else** { outcome if false }

**Let's give it a go shall we!**

-   run line by line to understand the boolean logic (true and false)

-   change x to receive the opposite outcome

```{r intro to boolean, include=TRUE}

x = 1.1 # change me and run again below!

if (x < 1) { # if x is < than 1...

  print('x is less than 1') # print this message if TRUE

} else { # else means here than x is  greater than one

  print('x is greater than 1') # print this message if FALSE

}

```

## Operating on if else with Operators

Problem: We have a conditional statement based on a threshold that is a likely outcome.

X=1 is the metaphorical wrench that will break our if else machine!

-   run the code below

```{r throw the wrench, some more!, include=TRUE}

x = 1 # the wrench

# our machine
if (x < 1) { # if x is < than 1…    

  print('x is less than 1') # print this message if TRUE    

} else { # else means here than x is  greater than one    

    print('x is greater than 1') # print this message if FALSE  

  }

```

-   "x is greater than 1" but... but... this is FALSE! ("oh no!")

    -   the `if` statement asks if x is less than 1 -- it was not, it simply ran the remaining `else` output

### Use operators to save us from doom

option 1: using `|` for OR statement

```{r help yourself with OR, some more!, include=TRUE}

x = 1 # the value that throws the metaforical wrench on our code

if (x < 1 | x == 1) { # add  the OR statement!

  print('x is less than or equal to 1') # change your output to inform yourself

} else { # else means here than x is  greater than one

  print('x is greater than 1') # print this message if FALSE
}

```

option 2: using `&` or AND statement

```{r help yourself with AND, include=TRUE}

x = 1

if (x < 1 & x != 1) { # add & for x not equal to 1

  print('x is less than 1') # added more information for this output

} else { # else means here than x is  greater than one

  print('x is greater than or equal to 1') # print this message if FALSE
}
```

#### What if you want to add another statement? use `else if`

`else if` - if your first `if` statement is false, `else if` provides another opportunity before defaulting to the `else` output

-   note you can have as many `else if` statements that you's like - just remember to keep organized and logical

option 3: add `else if`

```{r else... if..?, some more!, include=TRUE}
x = 1   

if (x < 1 ) { # if x is lass than 1      

  print('x is less than 1') # output if TRUE

} else if (x == 1) {

  print('x is equal to 1, wrench removed - your machine lives')

} else { # else means here than x is  greater than one     

  print('x is greater than or equal to 1') # print this message if FALSE  

  }
```

### Activity 1: The Sunday scaries (ooooo!)

#### *Imagine* it is mid-July and the weather has been beautiful and warm. You had an amazing weekend and you don't want it to end.

#### "...oh ..hmm that *muuust* be next week ..oh no!"

#### A jolt of shivers runs down your spine, it is after 5 pm on Sunday already! You just remembered you are leading a meeting tomorrow morning!

-   Objective: edit the time and your preparedness to receive the output `just blame it on the kids and stay home tomorrow`
-   Understand the `if`, `else, and else if` conditional statement with operators to solve!
-   a chunk is created below, fill the variables and learn your destiny

```{r sunday scaries, include=TRUE}
#  install.packages('lubridate') # if you do not have it already
library(lubridate) # converts the hour and minutes you input into an integer,


# assign your variables
day    =  # hmm.. what day is it?

time   =  as.numeric(hm('00:00')) # input military time, curently midnight 'hm' lubridate

ready  =   # add whether you are ready as 'yes' or 'no' o include  the quptes as a string


# run the conditional statement and learn your destiny

if (day != 'Sunday' & ready == 'no') { # the pseudosunday scaries

  print('Phew! Blissfully procrastinate more')

} else if (day == 'Sunday' & ready != 'no' & time < as.numeric(hm('17:00'))) { # almost forgot that you are awesome

  print('Oh yeah - you prepared last week! You are a badass, enjoy your time in the sun.')

} else if (day == 'Sunday' & ready != 'no' & time > as.numeric(hm('17:00'))) {

  print('Popcorn time')

} else if (day == 'Sunday' & ready == 'no' & time < as.numeric(hm('17:00'))) {

  print('Palms sweaty, eyes twitching - become awkwardly quiet and stiff. You scramble to finish your wide-eyed goodbyes to your friends as you inch closer to the exit. The computer calls out to you, finish the task if your life depends on it.')

} else {

  print('Just blame it on the kids and stay home tomorrow') # print this message if FALSE
}
```

### Activity 2: Life's obstacles

#### *Imagine* you're on the way to work, it's Monday - time to show that meeting what you got!

#### The speed limit to work is 25 mph the whole way, if you don't speed you will be late... you *caaan't* be late *again!*

#### Careful! You need to navigate your speed, the weather, and your caffeine intake (or lack thereof) to avoid getting into an accident, a speeding ticket, or worse!

-   Objective: fit the story! use operators to edit each `if`, `else, and else if` conditional statement

-   a chunk is *started* below

```{r lifes obstacles, include=TRUE}

#  install.packages('lubridate') # if you do not have it already
library(lubridate) # converts the hour and minutes you input into an integer


# assign your variables
weather     =   # rain or shine, you choose

speed_mph   =   # is your foot made of feather or lead?

coffee      =   # yes or no; decaf or regular; your choose


# what will it be you coding coder you?

if ()  { # you're a caffeinated getaway driver navigating a sunny day in the burbs like a bandit

  print('Made it safe and sound, 15 minutes early!')

} else if () { # caffeinated or not, its pouring cats and dogs so you follow the man's rules

  print('Made it safe and sound, but late. Luckily, everyone was late becasue of the sudden storm.')

} else if () { # left home like an uncaffeinated bat out of hell!

  print('Lets hope your liscence and registration is in the glove compartment!')

} else if () { # speeding in the rain, you hydroplaned and missed your meeting ..some say you're still spinning   

  print('Woweeeee!')

} else {  # the weather and caffeine withdrawal spell the perfect storm to turn this car around!

  print('Turn around and take the meeting from zoom')
}
```
