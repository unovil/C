# #define and const

## Constant

- sometimes necessary in a program such that the value will never change

```c
circumference = 3.14159 * diameter;
// constant 3.14159 is pi
```

### Reasons to use a constant than a literal

- you can ensure that this placeholder of a value will never change
- names tell you way more than numbers do

```c
interest = principal * 1.15 * time;
// it's a lot more useful to use the name 'rate' than 1.15

interest = principal * rate * time;
```

- what if the constant is frequently used and it needs to change value?
    - you only alter definition of symbolic constant, not every occurence of that in the program

### C90 and const

- C90 added another way to make symbolic constants
    - use `const` to convert declaration for a variable into declaration for constant

```c
const int MONTHS = 12; // MONTHS is symbolic constant for 12
const char message[] = "Eyyyy";
```

- `MONTHS` is read-only
- `const` is more flexible than `#define`
    - lets declare a type (type-safe)
    - allows better control over the program

(you can also use `enum` for making 'constants' [but not fully])

### Protection

- declaring something (like a string) as a const will make it protected from being modified explicitly
    - any attempt will result in error message from the compiler

```c
const char something[] = "Hiii";
strcpy(something, "Hello"); // results in error
```

## #define

- a preprocessor directive to define constants of most types

```c
#define PI 3.14159
#define WELP "WATETETETETEETETETE"
```

- when the program is compiled, that value is substituted everywhere there is `PI`
    - you can't assign any other value to it

- the `#define` statement has special syntax
    - no equal sign
    - no semicolon
  
- can appear anywhere in the program (global)
    - usually coders would put this at the start of the program or in an include file

- this statement helps programs more portable across many computers
    - example: use constant values related to the computer the program is running on
