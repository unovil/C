# Table of Some Other Useful Functions for Strings

| function                                          | purpose                                                      |
|---------------------------------------------------|--------------------------------------------------------------|
| `strchr(), strstr()`                              | searches character or substring in string <br>uses `string.h` |
| `strtok()`                                        | tokenizes a sequence of characters                           |
| `islower(), isupper(), isalpha(), isdigit()` etc. | for analyzing strings                                        |

## What's a Token?

A token is a sequence of characters that is separated by a delimiter

- a delimiter is just a character that has some special meaning (spaces, commas, periods, etc)
- breaking a string into many parts is called tokenizing

## Concept of Pointers

- C provides a useful variable type called a pointer
    - variable stores an address
    - its value is address of a location in memory that could contain a value
    - (we've used addresses with `scanf()`)

- Pretty confusing
    - Many languages usually have a smart way of getting rid of variables and memory (like Java)
    - C won't do that

```c
int num = 25;
int *pNum = &num;
```

- we declared a pointer `pNum` that contains where `num` is stored (its address)
    - pointers have a special syntax (like when * is used in declaring pointer)

- calling `pNum` will get you the address of `num`, not its value
    - to get value of `pNum`, you use an asterisk to dereference the pointer

    ```c
    printf("%d", *pNum) // prints 25
    ```

- `*` is dereference operator
    - effect is to access data stored at the address specified by pointer

- many string functions return pointers
    - don't worry if the concept doesn't sink immediately
    - brief mentioning because string functions return pointers

<img
  src = "../pictures/pointer example.png"
  alt = "Pointer example"
  style = "display: block; margin-left: auto; margin-right: auto"/>

- This shows the underlying mechanism of a pointer.
    - Both variables have their own address,
    - `Number`'s value is 25, while `pNumber`'s value is the address of (where the memory is stored) `Number`.

- `pNumber` will not point to the value of `Number`, only where that value is.

# Searching

## `strchr()`

- `strchr()` searches a string for some character
- first arg is string to be searched (address of char array)
- second arg is character to look for

- function searches for string from the beginning
    - returns' pointer to first position where char is found
    - to store return value, you create a variable to store address of character (pointer)

- if no char is found, function returns `NULL`
    - `NULL` is just `0` for a pointer
    - says that the pointer doesn't point to anything

```c
char str[] = "The quick brown fox";  // string to be searched
char ch = 'q';                       // character to search
char *pGotIt = NULL;                 // initialize pointer to NULL (does not point anywhere)
pGotIt = strchr(str, ch);            // stores address where ch (q) is found in string
```

## `strstr()`

- most useful of the searching functions
    - searches a string for occurrence of substring
    - returns pointer to position in first string where substring is found
    - if nothing, return `NULL`

```c
char text[] = "Hello there, name is Uno!"; // string to be searched
char word[] = "there";                     // substring to search
char *pFound = NULL;                       // initialize pointer to NULL
pFound = strstr(text, word);               // stores address where substring "there" is found
```

- searches text for first occurrence of substring in string
    - `there` appears at seventh char in text
    - `pFound` is set to address of `text` + 6
    - the search is case-sensitive

# Tokenizing

- tokenizing is breaking a sentence into words
- use `strtok()`
    - requires two arguments
    - string to be tokenized
    - string containing all delimiters

```c
#include <string.h>
#include <stdio.h>

void main() {
  // set delimiter
  const char delimiter[] = "-";

  // set string
  char str[80] = "Hello, how are you? - My name is - Uno";

  // set pointer to address of 
  char *token = strtok(str, delimiter);

  while (token != NULL) {
    // prints a string with delimiter until it finds next delimiter
    printf("%s \n", token);

    // putting NULL as the first argument tells strtok to 
    // continue searching on string you passed earlier;

    // token will be NULL if strtok can't find a delimiter
    token = strtok(NULL, delimiter);
  }
}
```

# Analyzing (usually on chars) from `ctype.h`

<img
  src = "../pictures/string analyzing functions.png"
  alt = "Analyzing Strings"
  style = "display: block; margin-left: auto; margin-right: auto"/>

- argument to each is character to be tested
- all return
    - `int` 1 if the character being tested is true
    - `int` 0 if the character being tested doesn't meet requirements
- return values convert to `true` and `false`, so you can also use `Bool`

```c
/* Program 6.8 Testing characters in a string */
#include <stdio.h>
#include <ctype.h>
int main(void) {
  char buffer[80];        /* Input buffer */
  int i = 0;              /* Buffer index */ 
  int num_letters = 0;    /* Number of letters in input */
  int num_digits = 0;     /* Number of digits in input */

  printf("\nEnter an interesting string of less than 80 characters:\n");
  gets(buffer);             /* Read a string into buffer */

  while (buffer[i] != '\0') {
    if ( isalpha(buffer[i]) )
      num_letters++;        /* Increment letter count */

    if ( isdigit(buffer[i++]) )
      num_digits++;         /* Increment digit count */
  }

  printf("\nYour string contained %d letters and %d digits.\n",
        num_letters, num_digits);

  return 0;
}
```
