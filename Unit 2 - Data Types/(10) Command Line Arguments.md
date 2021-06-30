# Command Line Arguments

* there are times when the user needs to enter a small amount of information at the terminal to develop the program

* There are two ways of handling this:
    1. to request the data
    2. to supply the information to the program at the time of execution (command-line args)
* we know that `main()` func is special in C
  * entry point of program
* when `main()` is called by runtime system, there are two arguments passed:
    1. `argc` (argument count), an int that specifies number of arguments typed on command line
    2. `argv` (argument vector), array of character pointers (str)

* first arg of `argv` is program name
* second arg of `argv` is command line argument

This is how it works:

```c
#include <stdio.h>

int main(int argc, char* argv[])
{
    int noa = argc;
    char* arg1 = argv[0];
    char* arg2 = argv[1];

    printf("No. of Arguments: %d\n", noa);
    printf("Arg. 1 is the program name: %s\n", arg1);
    printf("Arg. 2 is command line argument: %s\n", arg2);

    return 0;
}
```

```cmd
No. of Arguments: 1
Arg. 1 is the program name: D:\Documents\C Repos (Visual Studio)\Testing\Debug\Testing.exe
Arg. 2 is command line argument: (null)
```

* normally it would print (null) since there are no command line arguments passed
* if your IDE can pass arguments, you should do so, the number of arguments should rise as you pass more arguments
  * some IDEs available for this are Visual Studio and Codeblocks
