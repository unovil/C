# Displaying Output
## Overview
* The `printf()` function displays output to the screen.
```c
#include <stdio.h>

int main()
{
    printf("Something"); // this printf()
    return 0;
}
```
* a standard library function
    * outputs info to *standard output stream*, usually the command line
    * info displayed is the info between the parentheses of `printf("This part")`
    * the line ends with a semicolon `;`