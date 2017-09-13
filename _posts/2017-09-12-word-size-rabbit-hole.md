---
layout: post
title: word size rabbit-holes
---

Today's adventures in assembly are all about the importance of memory alignment for variable storage. Apparently, if you believe things on the internet, all modern processors read memory segments on word boundaries. Therefore, if you want to maximize efficiencies of accessing data in memory, you should declare your variables so that they align on word boundaries.

Obvs, this is not always possible. Hyde gives an example of this in C3.5, first showing declaration of some variables without regard to alignment and then with the declarations rearranged so the variables are declared starting on word boundaries, some of the vars are double-words, then words, then bytes.

I'm not in a position today to test this out, but suspect before long, a few more late nights, I'll be able to put this to the test and see how performance is impacted... today is not that day.

You can find discussions of this on stackoverflow and elesewhere. We never talked about this in my comp sci classes or more likely, if we did, I wasn't paying attention.