# Overview

- Function is a container of program code that accomplishes a particular task
- syntax rules define struct of function and how to use it
- same as subroutines or procedures in other languages
- some cause an action to take place

    ```c
    printf()
    ```

- others return a value for the program to use

    ```c
    strlen() // how long a string is
    ```

# Advantages

- if an entire program was a main() function, it's hard to test, debug, and maintain
- tasks can be divided into several subtasks
  - reduces complexity
  - separate functions written for each subtask
  - we can further divide each subtask into smaller subtasks that can reduce complexity even more
- reduce duplication of code
  - once a function is initialized, it can be used many times throughout program
  - reduces size of source code and reduces errors due to typos
- helps with readability
  - program is better organized
  - easier to read and fix
- allows only parts of a program to be tested and debugged independently
  - in the real world, many people are working on a program with thousands of lines of code
  - it's helpful that they can work independently
- functions developed in a program can be used in another program (software reuse)

## Black boxes

- many like to think of functions as boxes
  - information goes in as input
  - action and value it produces as output
- using this, people can focus more on how a function relates to the program (what it was meant to do) before writing anything

# Examples

- you already saw built-in functions like printf()
- notice how to invoke these and pass data?
  - arguments between parentheses following the function name
- for example

```c
printf(
    // first arg is usually a string literal,
    // succeeding arguments are variables and expressions (which may or may not exist)
)
```

# Implementing Functions

- just calling functions won't work unless we implement them
- we have to use built-in functions or write the code for the functions ourselves
- use descriptive function names to make it clear how that function works
  - if the functions are broad and general enough, you can use them in other programs

# `main()`

- as reminder, `main()` is a special function
  - indicates where program begins execution
- all C programs need to have `main()`
- you can pass data (command-line args)
- it can return data (error codes, opt)
