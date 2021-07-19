# Overview

- whenever defining a variable in C, compiler allocates correct amount of storage based on data type
- when we were assigning values to a pointer, we always used the address of an existing variable
    - because that variable already had memory allocated for it
    - what if you don't want to use another variable?
- regularly desirable to dynamically allocate storage while program is running
- if you have a program to read set of data from file to array in memory, you can
    - define array to contain maximum number of possible elements (fixed static size)
    - use variable-length array to dimension array size at runtime (dynamic until variable is defined)
    - allocate array dynamically using C's memory allocation routine

# Dynamic Memory Allocation

## First Approach

- you have to define array to contain maximum number of elements that would be read

```c
int data[1000];
```

- if data file has more than 1000 elements, program won't work
    - you have to change size to be larger then recompile
    - no matter what value you select, you can always run into the same problems

- using dynamic memory allocation functions, you can get storage on-the-go
    - no need to change the size

## Concept of DMA

- depends on concept of pointer, one of the big reasons to use pointers
- DMA allows memory to be allocated dynamically
    - possible because you have available pointers
- you can create pointers at runtime that are just large enough to hold amount of data you need
    - no memory wasted

## Heap Vs. Stack

- stack
    - memory set aside as scratch space for thread of execution
    - has a fixed size that is determined at compile-time
    - very easy to use, since it stores local variables and functions
    - since it's LIFO, the most recent block of memory that is unused will be the next used block of memory
    - managing this is as simple as moving a pointer
- heap
    - memory set aside for dynamic allocation
    - there is no enforced pattern to allocate and deallocate blocks
    - size is set on app startup, but can change when space is needed or not
    - much more complex and is slower than stack
    - it's manual to free the space allocated so it can be reused
  