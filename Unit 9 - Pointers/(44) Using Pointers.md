# Overview

- C offers basic pointer operations

- you can assign address to pointer
    - assigned value can be array name, variable preceded by `&`, or another pointer

- you can dereference pointer
    - use `*` to give value stored in location pointed to

- you can take pointer address
    - use `&` to tell where pointer is stored

- pointer arithmetic
    - `+` to add integer to a pointer
        - (integer is multiplied by number of bytes in pointed-to type and added to orginal address)
    - increment pointer by one (like when moving to next element in array)
    - `-` to subrract integer from pointer
        - (integer is multiplied by number of bytes in pointed-to type and subtracted from original address)
    - decrement pointer by one (like when moving to prev element in array)

## Uses of Arithmetic

- find difference between two pointers
    - example:
        - do this for two pointers to elements in same array
        - see how far apart elements are

- you can use relational operators to compare values of two pointers
    - pointers have to be same type

- two forms of subtraction:
    - subtract one pointer from another to get integer
    - subtract integer from pointer to get pointer

- incrementing or decrementing pointers can cause 'out of bounds' error
    - computer won't keep track of whether pointer still points to element

# Pointers in Expressions

- value referenced by pointer can be used in arithmetic

```c
int num = 0;
int *pnum = &number;
printf("%d", *pnum += 25);
```

- `*` indicates you're accessing contents of variable `pnum` is pointing to

- pointer can contain address of any variable of same type
    - you can use 1 pointer to change many variables' values
    - (as long as type-compatible)

```c
int main () {
  long num1 = 0L;                     // set variables
  long num2 = 0L;
  long *pnum = NULL;                  // initialize pNum

  pnum = &num1;                       // get address of num1
  *pnum = 2L                          // set num1 from 0L to 2L (indirect)
  ++num2;                             // increment `pnum`
  num2 += *pnum                       // add num1 to num2

  pnum = &num2;                       // now get address of num2
  ++*pnum;                            // increment num2 by 1 (indirect)

  printf("num1 = %ld\n", num1);
  printf("num2 = %ld\n", num2);
  printf("*pnum = %ld\n". *pnum);
  printf("*pnum + num2 = %ld\n", *pnum + num2);
}
```

## When receiving input

- when we used `scanf()`, we used `&` to obtain address of variable
- wen you have pointer that already has an address, you can use pointer name as argument for `scanf()`

```c
int value, *pvalue = &value;

printf("Input: ");
scanf("%d", pvalue);

printf("You entered %d.\n", value)
```

## Testing for NULL

- there is one rule: **NEVER DEREFERENCE AN UNINITIALIZED POINTER**

```c
int *pt;
*pt = 5; // GOOD LORD
```

- second line: store `5` in location where `pt` points
    - `pt` has random value, we will never know where `5` will be placed
    - might go somewhere harmless
    - might overwrite data or code
    - might cause crash

- creating pointer only allocates memory to store pointer itself
    - does not alloate memory to store data
    - before using pointers, it should be assigned a memory location already allocated
        - assign address of existing variable to pointer
        - or use `malloc()` to allocate memory

- to make sure that pointer won't point anywhere, use

```c
int *pvalue = NULL;
// also valid
int *pvalue = 0;
```

- `NULL` is special, represents pointer equivalent to 0
- because `NULL` is 0, to test whether `pvalue` is `NULL`, do

```c
if (!pvalue) {...}
// or
if (pvalue == NULL) {...}
```

- **always** check for `NULL` before dereferencing
    - often when pointers are passed to func
