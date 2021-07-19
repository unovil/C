# Overview

- we know that arrays are very related to pointers and pointer arithmetic
    - concepts are useful when applied to strings

- one of most common applications of pointer to arrays is pointer to string
    - uses notational convenience
    - very flexible

## Array Parameter vs `char*` Paramater

```c
void cpyStr(char to[], char from[]) {
  int i;

  for (i = 0; from[i] != '\0'; ++i) 
    to[i] = from[i];

  to[i] = '\0';
}
// for every index of i (except when it reaches \0 in from)
// to[i] = from[i], then set final to[i] to \0
```

```c
void cpyStr(char *to, char *from) {
  for ( ; *from != '\0'; ++from, ++to)
    *to = *from;
  
  *to = '\0';
}
// as from and to pointer moves until '\0'
// dereference and set *from to value of *to
// then dereference and set *to to \0
```

- first of all, pointer arithmetic is much faster than using arrays
- second, the pointer code is much more straightforward than array code

# Strings as Pointers

- since strings are just character arrays, the syntax is identical

```c
char text[] = "hello!";
char *ptext = text;
```

- `ptext` can use pointer arithmetic too

```c
++ptext; // moves to next char in string
--ptext; // moves to prev char in string
```

## Optimized Pointer Example

```c
#include <stdio.h>
#include <stddef.h>
#define CHAR_MAX 20

void cpyStr (char *from, char *to) {
  while (*from)         // since '\0' = 0 = false, it jumps out when it goes \0
    *to++ = *from++;    
    /* unary operators are now at the end 
       means that this is performed at the end of execution 
          for example: *to++ means to dereference *to then do the
          assignment THEN add 1 */

  *to = '\0';
}

int main(void) {
  char string1[CHAR_MAX] = "Some string here.";
  char string2[CHAR_MAX];

  cpyStr(string1, string2);

  printf("\"%s\"\n", string2);

  return 0;
}
```

```txt
"Some string here."
```
