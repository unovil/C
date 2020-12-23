# Comments

* used in a program to document it
* used to enhance readability
* to remind what the program or a particular line is doing
* ignored by the compiler

## Situations where comments can be useful
1. A programmer can return to a program he/she coded a long time ago and can still remember the purpose of a particular line of code
2. Not needing to re-understand the code, which saves a **lot** of time

## Syntax
There are **two** ways to add comments to a C program
1. using `/*`
    * marks start of comment
    * needs to be terminated
    * will continue being a comment until you end it with `*/`
    * everything between the two becomes part of the comment
    * known as a *multiline comment*
2. using `//`
    * this comments only the line where `//` is
    * known as a *single line comment*

For example:
```c
/* This is a multi-line comment.
Everything is part of this.
AND I MEAN EVERYTHING. */

// this is a single line comment
int main() {
    return 0; // you can even do this!
}
```

## Style
You can use this for showing who you are
```c
/*
Author: Uno Villegas
Purpose: to do something
Date: 2020
*/
```
You can also embellish comments to make them 'urgent'
```c
/******************************
* READ THIS COMMENT *
******************************/
```

## Actual Example of Using These
```c
/* 
This program adds two values and displays these results.
*/

#include <stdio.h>

int main(void)
{
    // 1. Declare the vars
    int first, second, sum;

    // 2. Assign the values
    first = 20;
    second = 30;
    sum = first + second;

    // 3. Display result in console
    printf("The sum of %i and %i is %i\n", first, second, sum);

    return 0;
}
```

## Use of Comments
* it's possible to insert too many comments. this can degrade the readability of the program.
* use comments intelligently
* insert comments while typing your code, so the logic is still fresh in your mind.
* put comments on every line you think is confusing, or if you think the line is too complex.
* comments help on debugging and finding out logic errors
* 