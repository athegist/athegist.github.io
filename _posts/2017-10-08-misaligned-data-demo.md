---
layout: post
title: mis-aligned data demo
---

Early in the book, Hyde asserts that there are performance benefits to working 
with data that is aligned on word boundaries. In today's reading, he proves it.

ConstDemo.hla is a simple program that sets up a couple loops. In the first, a
misalignment of the data is forced, which slows down processing as the CPU has
to read extra bits in order to get to the relevant data being processed in the 
loop.

The user is prompted to time the loop with a stopwatch. As I have the program
configured on my laptop (an eight year old MBP i7), it takes about 40 seconds
for this first loop to finish.

Next the program loops over the data again, but this time the data has been
realigned on word boundaries and the run time is about half.

So, aligned data makes a difference in performance.

[ConstDemo](https://github.com/athegist/asm0/blob/master/C4/ConstDemo.hla) <br />
