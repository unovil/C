# Returning Data

- in our prior example (#27), the `multiply` function displayed the results through the command line
- you might not always want calculations to be displayed immediately
  - functions can return data with specific syntax

# return type

- you can specify the type of value to be returned as any legal type in C
  - includes enumeration and pointers
- can also be type `void`, no value is returned

# `return` statement

- basically the exit of a function (like `break` in a loop)

```c
return;
// if you do this without putting any value, it's basically an exit statement
```

- this form of `return` is used exclusively for `void` functions, as a means of an exit

- the more general form is

```c
return expression;
```

- this form needs to be used when return value type is not `void`
- the value returned from the invocation is the value that results when expression is eval

# Returning Data

- when function has statements in the body but doesn't return anything must be of `void`
  - you'll get an error when `void` returns a value
- non-`void` function needs to return value of specified data type
  - you'll get error when return type is different
- if expression results in value that's different from return type, compiler inserts conversion from type of expression to required
  - produces error when not possible
- you **can** have more than one return statement, but it makes readability a bit more difficult

# Invoking Function

- use function name followed by arguments
- values of arguments are assigned to params in function
- when function executes, computation proceeds using values as arguments
- arguments should agree in type, number, and sequence of parameters

# Assigning data returned

- if function is used on right side, return value is substituted for the function

```c
int x = FunctionCall();
```

- calling function doesn't have to recognize value returned from called function
- up to you on how you use the values returned

# Example

```c
#include <stdio.h>

int multiply (int x, int y)
{
    int result = x * y;
    return result;
}

int main (void)
{
    /* var result will not interfere with 'result' in the function, 
    since the function 'result' only exists within that function, 
    exiting function removes the memory inside */

    int result = 0;
    result = multiply (10, 20);

    printf("return is %d\n", result);

    return 0;
}
```

```txt
return is 200
```
