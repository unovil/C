# Accessing Pointer Values

- use the indirection operator (aka dereference) `*` to get value of variable pointed by pointer

```c
int number = 15;
int *pnumber = &number;
int result = 0
```

- `pnumber` contains address of `number`
    - use in an expression for calculating `result`

```c
result = *pointer + 5; // result = 20
```

- `*` is also used for multiplication
    - depending on where it appears, compiler will know whether it's an indirection oper, multiplication sign, or part of type specification
    - context determines

```c
void main(void) {
  int count = 10, result;
  int *int_pointer;

  int_pointer = &count;
  result = *int_pointer;

  printf("count = %i, x = %i\n", count, result); // count = 10, x = 10

  return 0;
}
```

# Displaying Pointer Value

- outputting address of a variable uses format spec `%p`
    - outputs memory address in hexadecimal

```c
int number = 0;                           // int var initialized as 0
int *pnumber = NULL;                      // pointer points to type int

number = 10;
pnumber = &number;
printf("pnumber's value: %p\n", pnumber); // output value (address)
```

- pointers have 8 bytes and addresses have 16 hexadecimal digits
    - if machine has 64-bit system, compiler can support 64-bit addresses (16 hexa)
    - some compilers use 32-bit addressing, so addresses are 32-bit (8 hexa)

## Displaying Pointer Address

- a pointer itself has an address, like any other variable
    - use `%p` for format specifying
    - use `&` (address of) to reference address that variable occupies

```c
printf("number's address: %p\n", &number);
printf("pnumber's address: %p\n", (void*) &pnumber);
```

- for displaying pointer addresses, cast to `void*`
    - prevents possible warnings
    - `%p` expects value to be a pointer pointing to a type
        - but, type of `&pnumber` is 'pointer to pointer to int'

# Displaying number of bytes pointer is using

- use `sizeof` to get number of bytes pointer occupies
    - as of writing, my machine shows pointer has 8 bytes
    - means that memory address is 64 bits

```c
printf("pnumber's size: %d bytes\n", sizeof(pnumber));
```

- you may get compiler warning when using `sizeof` this way
    - `size_t` is implementation-defined `int`
    - to prevent, cast argument to type `int`

```c
printf("pnumber's size: %d bytes\n", (int) sizeof(pnumber));
```

# Final Example

```c
#include <stdio.h>
#include <stdlib.h>
#include <stddef.h>

void main()
{
  /* initialize */
  int number = 5;
  int *pnumber = NULL;

  printf("number's address: %p\n", &number); // output number address
  printf("number's value: %d\n\n", number);  // output number value

  /* set address of number */
  pnumber = &number

  printf("pnumber's address: %p\n", (void*) &pnumber);    // output pnumber address
  printf("pnumber's size: %zd bytes\n", sizeof(pnumber)); // output size of pnumber
  printf("pnumber's value: %p\n", pnumber);               // output value of pnumber (address of number)
  printf("pnumber points to: %d\n", *pnumber);            // output value of var pnumber points to
}
```

```txt
number's address: 0xffffcbfc
number's value: 5

pnumber's address: 0xffffcbf0
pnumber's size: 8 bytes
pnumber's value: 0xffffcbfc
pnumber points to: 5
```
