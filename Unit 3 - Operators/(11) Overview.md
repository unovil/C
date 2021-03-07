# Overview
* operators are functions that have symbolic name
* they perform math or logic operations
* operators are predefined in C, and most tend to be in the middle of two data

logical operator
- also a "Boolean operator"
- returns Boolean result based on one or two other expressions

arithmetic operator
- math function takes two operands and performs calculation

other operators
- assignment (`=`), relations (`<, >, !=, ==`), bitwise (`<<, >>, ~`)

# Expressions and Statements
Statements
- basic program steps of C
- most are constructed from expressions

Expressions
- a combination of operators and operands
    - operands are what operator operates on
    - operands can be constants, variables, or combination
    - every expression has a value

## Types of Statements
Simple Statement
- ends in semicolon `;`
```c
int Miguel; // declaration
Miguel = 5; // assignment
printf("Miguel"); // function call
while (Miguel < 20) Miguel = Miguel + 1; // structure
return 0; // return
```

Compound Statement
- two or more statements grouped by braces (block)

```c
int index = 0;
while (index < 10)
{
    printf("hello");
    index = index + 1;
}
```