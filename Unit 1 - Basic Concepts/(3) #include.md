# The `#include` statement
## Overview
* a preprocessor directive
* In our program, we used `#include <stdio.h>`
* not strictly part of the executable, but the program won't work without it
* compiler is instructed to **include** the contents of the file with the name `stdio.h` to the program
    * the `.h` is an extension for files called *header files*
    * called a header file because it's usually at the head of the source file

## Header Files
* define info about some functions provided by that file
* `stdio.h` is the **standard C library header** and provides functions for output, among other things
* we need to have this for the `printf()` function
* contains information that the compiler needs to know what `printf()` means, as well as other functions that associate with i/o
* `stdio` is short for **standard input/output**
* specify info that compiler uses to integrate predefined functions in a program
* similar to the `import` statement of Python

## Syntax
* names are case sensitive on systems, so write them in lowercase
* Two ways to use `#include`:
    1. using angle brackets
        * tells preprocessor to look for the file in one or more **standard sys. directories**
        ```c
        #include <uno.h>
        // ...
        ```
    2. using double quotes
        * tells preprocessor to **first look** in the **current directory**
        ```c
        #include "uno.h"
        // ...
        ```
* evey compiler that conforms to the C11 standard has a set of standard header files
* you should use `#indef` and `#define` to protect against multiple inclusions of header file