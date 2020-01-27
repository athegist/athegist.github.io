---
layout: post
title: copy by reference
---

In this exciting episode of not learning asm by working through a book called,
++The Art of Assembly Language++, we write the program linked below, which 
features a string that we input, that is copied to another string *by reference*.

Copy by reference, means we're not actually making a new string, but rather
we're a new object in memory that simply points to the first one. This *copy by
reference* is really just copying a pointer. In HLA, strings are pointers.
Copying a string by reference, is just copying the pointer.

[copy by ref](https://github.com/athegist/asm0/blob/master/C4/strRefAssignDemo.hla)