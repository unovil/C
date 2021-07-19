# String Functions

- strings are not a variable type in C
    - you can't use operators on it
    - hello

## Common Operations on Strings

| function              | purpose                     |
|-----------------------|-----------------------------|
| `strlen`              | length of a string          |
| `strcpy(), strncpy()` | copying a string to another |
| `strcat(), strncat()` | concatenating two strings   |
| `strcmp(), strncmp()` | if two strings are equal    |

- C library supplies thes in `string.h`

## Getting Length of a String

- use `strlen()`
    - return is type `size_t`
    - won't include null character in counting

```c
#include <stdio.h>
#include <string.h>

void main() {
  char myString[] = "four";
  printf("The length of the string is %d", strlen(myString));  // 4
}
```

## Copying Strings

### strcpy()

- since you can't assign arrays, you also can't assign strings

```c
char s[100]; // declaration
s = "hello"; // assignment won't work (lvalue required)
```

- you can use `strcpy()` to copy string to an existing string
    - basically string equivalent of `=`

```c
#include <stdio.h>
#include <string.h>

void main() {
  char dest[50];
  // strcpy(where to paste, what to copy)
  strcpy(dest, "Copied string");
  
  printf("The length of the string is %s", dest);  // Copied string
}
```

### strncpy()

- `strcpy()` won't check if the src string actually fits in dest string
    - if the src is larger, then an error would happen

- better to use `strncpy()` for copying strings safely
    - accepts 3 arguments (destination, source, max num of char strncpy will copy)

```c
char src[40];
char dest[12];

memset(dest, '\0', sizeof(dest)); 
/*  
fills all of dest with null char so 
we won't have to worry about copying
*/
strcpy(src, "Hello what are you doing?");

strncpy(dest, src, sizeof(dest) - 1); 
/* 
copies "Hello what " into dest 
we use a - 1 to save space for the null character that memset put in
this is important as not doing so will cause overflow and allocation probs
*/
```

## String Concatenation

### strcat()

- use `strcat()`
    - copy of second string is added to end of first
    - combined version overwrites first string
    - second string is not altered

- `strcat()` will return the concat. string AND change the first argument

```c
char myString[] = "my string";
char input[80];

printf("Enter string to be concatenated: ");
scanf("%s", input);

printf("\nThe string %s concatenated with %s is %s", 
       myString, 
       input, 
       strcat(input, myString);

printf("\nThe 1st argument is now %s", input); // input & myString
```

### strncat()

- `strcat()` has the same problem as `strcpy()`
    - they both fail to allocate the correct number of characters

- you can overflow the system and cause malloc problems
    - use `strncat()` instead
    - also uses 3 args

```c
char src[50], dest[50];

strcpy(src, "This is the source.");
strcpy(dest, "This is the destination.");

strncat(dest, src, 15);
/* 
  the '15' affects src
    - it only adds the first 15 characters from src
*/
printf("Final destination is \"%s\"", dest);
```

## Comparing Strings

### strcmp

- you can't use `==` for comparing strings
    - it only checks if both strings have same address

- use `strcmp()`
    - this won't compare arrays, so it can compare strings with different array sizes
    - this won't compare characters
        - you can only use strings "app" and "A" but not char 'A'

### strncmp

- strcmp compares strings until it finds corresponding characers that differ
    - could compare until the end

- strncmp compares strings until it has compared a number of characters specified by third argument

```c
if (strncmp("astronomy", "astro", strlen("astro")) == 0)
  printf("Found: astronomy");
  // Found!

if (strncmp("astounding", "astro", strlen("astro")) != 0)
  printf("Not in: astounding");
  // Not in.
```

### Return Values

| return value | desc                             |
|--------------|----------------------------------|
| `0`          | two strings are same and nonzero |
| `-1`         | str1 is less than str2           |
| `1`          | str2 is less than str1           |

- it compares their ascii values
