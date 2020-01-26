---
layout: post
title: pointer problems
---

In chapter four, Hyde introduces a variety of data types and declarations,  
including how to declare and use constants, scalar variables, integers, reals,  
"data types", pointers, arrays, records/structures, unions and namespaces.  

Hyde's HLA includes the concept of constants, as I understand them -- a named  
element assigned some value that cannot change during compilation or execution.  
But oddly, HLA includes *VAL*s as well. These are "constants" that can change  
value during compilation and execution. What distinguishes them from normal  
variables, isn't clear to me yet.  

This chapter also includes coverage of pointers and common issues with their
usage including:
* Using an uninitialized pointer
* Using a pointer that contains an illegal value (e.g. NULL)
* Continuing to use *malloc'd* storage after that storage has been freed
* Faling to free storage once the program is done using it
* Accessing indirect data using the wrong data type