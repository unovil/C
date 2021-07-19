# Declaring Pointers

- pointers are not declared like normal vars

```c
pointer ptr; // not how you declare
```

- not enough to say that variable is pointer
    - you have to specify kind of variable pointer points
    - different types take up different amounts of storage
    - some operations need knowledge of that size

- you can declare a pointer to a variable of type `type` with:

  ```c
  type *ptr;
  // example:
  int *pnumber;
  ```

- type of var with `pnumber` is `int*`
    - can store addresses of any `int` var

```c
int * pi;          // pi is pointer to an int var
char * pc;         // pc is pointer to a char var
float * pf, * pg;   // pf and pg are pointers to float vars
```

- space between `*` and pointer name is optional
    - coders use space in declaration
    - they omit it when dereferencing a var

## Storage

- value of pointer is an address, an unsigned integer on most systems
    - you shouldn't think of pointers as ints
    - there are things you can do with integers and not pointers, vice versa
        - you can multiply integers, but not pointers, for example
- pointer is a new type
    - format specifier: `%p`

## Initialization and `NULL`

- **always** initialize a pointer when you declare it
    - in above example, I just showed how to declare it
    - very dangerous if pointer is not initialized

- if you don't know what to point it to at declaration, use `NULL`
    - pointer will not point to anything

```c
int *pNum = NULL;
```

to use `NULL`, add `#include <stddef.h>`

- `NULL` is constant in stdlib definitions
    - the `0` equivalent for pointers  
- using `NULL` guarantees pointer will not point anywhere in memory
    - prevents accidental memory overwrite by using pointer that does not point anywhere

# Address Of

- when initializing pointer with address of variable, use `&`

```c
int number = 99;
int *pNumber = &number;
// pNumber now contains the address of number
```

- initial value of `pNumber` is address of `number`
    - declaration must precede initialization of pointer
    - compiler must have allocated space (thus the address) for `number` to initialize `pNumber`

# Being careful

- there is nothing special about declaring pointers
    - you can even have group declarations

```c
double value, *pVal, fnum;
// only pVal is a pointer
int *p, q;
// only p is the pointer
// common error to think both p and q are pointers
```

- good idea to use names starting with `p` for pointer names
