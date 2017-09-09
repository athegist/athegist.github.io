---
layout: post
title: Dates as packed data
---

Today's adventures in asm, courtesy of Mr. Hyde, have me packing dates of the form mm-dd-yy, cough (terrible), into a one and two byte locations in memory (al and ax and possibly other non-register locations, it's a bit opaque to me at this point). Ultimately everything fits into two bytes, though at first glance it may seem like more would be required.

There are only 12 months, so months can be represented in a nibble or four bits. Four bits can represent 16 different values.

There are a maximum of 31 days, so days can be represented in five bits. Five bits can represent 32 different values.

There are 100 possible year values, 0-99, so that will require seven bits for coverage. Seven bits can represent 128 different values.

Four and five and seven... 16 bits, two bytes.

The code prompts the user for mm dd yy. Assuming the user enters things correctly, mm is stored initially in the four low order (right-most) bits of al, maybe it looks something like this for January.

0000_0000_0000_0001

We then shift this to the left by five, because we need to store the day, so we need the right-most five bits for that, this gives us:

0000_0000_0010_0000

Then we `or` al with our day value, so for simplicity, let's say we're dealing with January 4, we now have:

0000_0000_0010_0100

Next our code shifts ax left by seven, so we end up with:

0001_0010_0000_0000

Now we have low order bits freed up to hold our year, seven bits. If our year is 70 our new binary arrangement is:

0001_0010_0100_0110

The decimal value of the two bytes above, 4678, is meaningless for the data we're storing. Remember, we've packed our date string into this two byte value to maximize our storage efficiency. Computationally, packing and unpacking this data is not the most efficient, there's a trade off here for computation to save storage.

There's a couple different versions of the program in the repo now. One that is straight from the book and one that provides more output, an annotated version, if you will.

[dateDemo](https://github.com/athegist/asm0/blob/master/C2/dateDemo.hla)
[dateDemoAnnotated](https://github.com/athegist/asm0/blob/master/C2/dateDemoAnnotated.hla)