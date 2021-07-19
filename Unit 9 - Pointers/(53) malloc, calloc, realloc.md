# `malloc` - memory allocation

- simplest stdlib function to allocate memory at runtime
    - you have to include `stdlib.h`
- specify number of bytes of memory to allocate as argument
    - returns address of first byte of memory that it allocated
- because it's an address, you can only put it in a pointer

```c
int *pNum = (int*) malloc(100);
// store 100 bytes of memory
// since malloc returns a void address, you have to cast it to int pointer
// store address to pNum
```

- `pNum` will point to first location at beginning of 100 bytes allocated
    - it can hold 25 or 50 `int` values, depending on the system
    - this is because each `int` value is 2 or 4 bytes large
- we're working based on an assumption which could change depending on the computer
    - to fix this, we use the `sizeof` operator

```c
int *pNum = (int*) malloc(25 * sizeof(int));
```

- now this memory allocated will **always** have the capacity for 25 `int` values

## Limitations

- you can request any number of bytes
- if memory requested can't be allocated for some reason
    - returns pointer with value `NULL`
- always good idea to check any dynamic memory request with `if`
    - make sure memory is really there before you use it

```c
int *pNUm = (int*) malloc(25 * sizeof(int));
if (!pNum) {
  // code to deal with failure...
  // PLEASE, IF THIS FAILS ABORT THE PROGRAM IMMEDIATELY
  // if the program can't allocate memory, it can crash and lead to memory problems
}
```

# `free` - de-allocating memory

- when allocating memory dynamically, it's your responsibility to release it when not required
    - memory is a vital resource!
- memory allocated on heap will be automatically released when program ends
    - better to release the memory when you're done, even before exiting the program

```c
free(pNum);
pNum = NULL;
```

- `free(0)` function has parameter of `void*`
    - you can pass any pointer
- as long as `pNum` contains address returned when memory is allocated
    - entire block of memory is freed for further use
- you should always set it to `NULL` after memory is released

## Memory Leak

- occurs when you allocate some memory dynamically and can't retain the reference, so you can't release memory
- often within a loop, when it's out of scope
- because you can't release the memory
    - program consumes more and more of the available memory on every iteration
    - eventually, program occupies all memory and it crashes
- to free dynamic memory, you need access to the address to that memory block

# `calloc` - contiguous allocation

- similar to `malloc`, though with a few advantages
- it allocates memory as number of elements of some size
    - initializes memory allocated such that all bytes are 0
- arguments
    - number of data items where space is required
    - size of each data item

```c
int *pNum = (int*) calloc(75, sizeof(int));
// initalizes 75 blocks of memory for int
// cleaner and safer since it initializes the blocks
```

- return value is also `NULL` when memory can't be requested
- big advantage over `malloc` is you know the memory area is initialized to 0

# `realloc` - re-allocating memory

- `realloc()` reuses or extends memory you previously allocated with `malloc()` or `calloc()`
- arguments
    - pointer with address returned by call to `malloc()`/`calloc()`
    - size in bytes of new memory to allocate
- allocates amount of memory specified by second argument
    - contents are **not** erased, they are retained
- returns `void*` to new memory or `NULL` if memory fails to be requested

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef unsigned long ul;

int main(void) {
  char *str;

  // since 1 char is 1 byte, using malloc is fine
  /* Initializing */
  str = (char *) malloc(10);
  strcpy(str, "uno");
  printf("String = %s, \t\tAddress = %lu\n", str, (ul) str);

  /* Re-allocating */
  str = (char *) realloc(str, 15);
  strcat(str, " villegas");
  printf("String = %s, \tAddress = %lu\n", str, (ul) str);

  /* freeing */
  free(str);
  str = NULL;

  return 0;
}
```

```txt
String = uno,           Address = 34359903376
String = uno villegas,  Address = 34359903376
```

# Guidelines

- don't allocate lots of small amounts of memory
    - allocating memory on heap carries some overhead
    - allocating many small blocks carry much more overhead than allocating fewer larger blocks

- only hang on to memory as long as you need it
    - when finished, release it

- ensure that yoy provide for releasing memory allocated
    - decide where in code to release it when allocated
    - don't make the freeing depend on other functions

- don't overwrite the address you have allocated on the heap
    - can cause memory leak
    - be careful when allocating memory in loop
