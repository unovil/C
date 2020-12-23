# Reading Input From The Terminal
## Overview
* useful to ask program user to enter data into program *via the terminal/console*
* the C lib. has many input functions, and `scanf()` is the most general, and can read a variety of formats
* reads input from the **standard input stream** `stdin` and scans input based on the **format provided**
    * can be a simple constant string, but you can specify `%s %d %c %f` etc... to read strings, integers, characters, floats, etc...
* if `stdin` is keyboard inpput then text is read ib because keys generate text characters: letters, digits, punctuation
    * when entering `2014`, type the characters `2, 0, 1, 4`
    * the program has to convert string char-by-char to a numeric value, that's the purpose of `scanf()`

## `scanf()`
* like `printf()`, `scanf()` uses control string followed by a list of args
    * control string : indicates destination data types for input stream of chars
* `printf()` uses variables, constants, and expressions as argument list, while `scanf()` uses pointers to variables
* 3 rules for `scanf()`
    1. returns # of items it successfully reads
    2. precede the variable name with an address `&` for reading a value into basic variable types (like integers) 
    3. don't use #2. for reading strings into character arrays

* uses whitespaces (newlines, tabs, spaces) to decide how to divide input to separate fields
* opposite of `printf()` which converts integers, floats, characters, and strings to text that is displayed onscreen

## `scanf()` example
```c
#include <stdio.h>
int main()
{
    // declaring some variables, namely str and i
    char str[100];
    int i;
    
    // get information from the user
    printf("Enter a value:");
    scanf("%s %d", str, &i); // str has no & yet i has & because i is an integer

    // prints the info it gathered
    printf("\nYou entered: %s %d", str, i);

    return 0;
}
```

## `scanf()` (part ii)
* when program uses `scanf()`, it pauses and waits for you to input something
* after that, it proceeds and reads the input
* it expects input in same format as you provided (`%s %d`)
* you have to provide valid input (*string* then *integer*)

So, when you compile and run the code, this is the result:
```bash
JHS-2695@DESKTOP-2EETME7 /cygdrive/d/Documents/C/projects
$ ./hello_world
Enter a value:hello 3 # the program is paused until you type somehting and press Enter
You entered: hello 3 # it shows the result of the conversion
```
