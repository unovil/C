# Overview

- array is collection of values of same type that we can refer to with name

- pointer is variable that has a memory address value
    - can reference another variable or constant of given type
    - can use pointer to hold address of different vars at different times

- arrays and pointers are closely related and can be used interchangeably at times

- one of most common pointer uses is pointers to arrays
    - notational convenience
    - program efficiency
    - result in code with less memory and faster execution

# Syntax

```c
int values[100];
int *pvalues;
pvalues = values;
```

- when defining a pointer to point to elements of an array
    - we don't have a type 'pointer to array'
    - designate pointer as pointing to value type of array

- no need to set it to `&values`, because `values` is a pointer
    - `values` points to first element in the group of 100 elements
    - compiler treats array name without subscript as pointer to said array

- specifying values without subscript produces pointer to first element

## Setting to Specific Elements

```c
pvalues = values;
// is the same as
pvalues = &values[0];
// gets the address of the first value in the array
```
