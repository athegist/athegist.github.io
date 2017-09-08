---
layout: post
title: Sign and zero extension
---

Today marks hitting some new material on the quest to learn asm. I vaguely recall dealing with sign and zero extension before, at least conceptually, but I don't recall having learned the instructions for these concepts.

```cbw (); Converts the byte in al to a word in ax via sign extension  
cwd (); Converts the word in ax to a double word in dx:ax  
cdq (); Converts the double word in eax to the quad word in edx:eax  
cwde(); Converts the word in ax to a double word in eax  ```