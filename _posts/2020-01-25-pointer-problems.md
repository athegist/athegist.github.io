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

The first issue is easily understood. When a pointer is declared, storage is
allocated for the pointer itself, but the pointer references address zero, 
rather than a memory address of the developer's choosing. If the developer does
not assign the pointer to a memory address to which they have access, the
results can be unpredictable. In my testing, a memory access violation was 
consistently thrown.

The second issue can arise when the developer miscalculates the address that 
they want to assign to a pointer and rather than pointing where it should, it
points somewhere it should not, not zero as in the previous example. In this
case, it may point to a location in memory that the program can access, but the
data there may not be correct for the application and this can result in errors
that are difficult to debug.

The third issue doesn't seem like a pointer issue as much as it is a memory
management problem. Attempting to access a pointer that references a freed
memory segment is a *use after free* issue and depending on the specifics, the
application could work just fine, could fail unpredictably and again may be 
difficult to troubleshoot.

Failure to free storage after use is again more of a memory management issue
than a pointer issue, in my mind, but could result in classic memory leaks.

The last issue arises because HLA and probably other languages that use
pointers don't enforce pointer-type-safety, meaning the compiler doesn't check
that the pointer being referenced is used in a type-safe manner. You may be 
treating the data at a given address as a character, when it should be treated
as double word hexadecimal -- the text has some example programs that cover
some of these issues.

