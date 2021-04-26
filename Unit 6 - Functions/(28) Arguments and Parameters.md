# Parameters and Arguments
- param is the variable in function declaration and definition/implementation
- when function is called, arguments are the data you pass
    - athe actual value of the variable
- func params are defined in function header
    - placeholders for args that need to be specified when func is called
## Parameters
- list of parameter names with types
- each param is separated by comma
- list of params is enclosed with `()` that follow func name
- if func has no params, put `void` between parentheses
- names of params are local to function
    - the arg values are assigned to respective params when function is called
- body of function should use params in implementation, otherwise why did it exist?
    - unless explicitly specified, variables in function cannot be used outside the func
- function can have additional locally def vars that are needed to be implemented
- when passing an array as arg
    - you must also use an additional arg specifyng size of array
    - function doesn't know how many elements are in that array
## Example
- when printf() is called, you always supply at least one argument
- params greatly increase usefulness and flexibility of function
- good idea to add comments before each function definition
    - helps readability

# Example Code
```c
#include <stdio.h>

void multiply(int x, int y)
{
    int result = x * y;
    printf("The product of %d and %d is %d\n", x, y, result);
}

int main (void)
{
    multiply(10, 20);
    multiply(5, 20);
    multiply(1, 2);
}
```

```
The product of 10 and 20 is 200
The product of 5 and 20 is 100
The product of 1 and 2 is 2
```
