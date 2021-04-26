# Overview
- when creating function, specify header as first line of function definition
    - followed by `{`
    - then the executable code in between
    - followed by `}`
- the executable code is called the function body
## Function Header
- defines name of function
- specifies parameters (number and types of values passed to function when invoked)
- type of value that function returns
## Function Body
- contains statements executed when function is invoked
- has access to the values u put in the params

```c
return_t Function_name (Paramaters separated by commas)
{
    // statements...
    return (value that is of type return_t);
}
```
# Meaningful Names
- first line of function def tells compiler 
    1. type of value it returns
    2. its name
    3. arguments it takes
- meaninful function and variable names are very important for readability
# Example
```c
void printMessage (void)
{
    printf("Printing\n");
}
// don't worry about void for now
// just that printMessage is a good function name because it describes what the purpose of the function is
```
- first line of `printMessage()` func tells compiler that function returns no value (keyword `void`)
- after that is function name (`printMessage`)
- after that it takes no arguments (second use of `void`)
## Can the function do nothing? **Yes**.
- statements can be absent, but braces must be present
- if no statements in body, return type should be `void`
- often useful in testing phase of complex program
    - allows to run program with only selected functions
    - then add statements to functions step by step and testing along the way until whole function is fully tested
# Naming Conventions
- names should be legal
    - not reserved word (`int`, `double`, etc.)
    - not same name of another function in program
    - not same name as any of stdlib functions
- other than that, naming is same as var
    - sequence of letters, digits
    - first char needs letter
    - underline char counts as letter
- should be meaningful and relevant to function purpose
## Naming Approaches
- often, function (and variable) names consist of more than one word
- either
    1. separate each word with underline
    2. capitalize first letter of each word
    3. capitalize after first word (camelCase)
- any convention is fine, just be consistent with it
# Function Prototype
- statement that defines function
    - has name, return value type, and type of each param
    - provides all external specifics
- writing is same as function header
    - difference is to add semicolon at end
- like declaring a variable but not yet initializing it
```c
void printMessage(void);
```
- enables compiler to generate appropriate instructions at each invocation
    - and checks the 'grammar' for errors
- when including a std header file, it adds function protoypes to the program
- usually appear at beginning of source file prior to implementations of any function OR in header file
- param names don't have to be same as those used in func def
    - not req to include param names in function prototype
- basically, function prototypes are placed BEFORE the main() so that there is no warning that it doesn't exist
## Example
```c
#include <stdio.h>

int main()
{
    add(); // sample function
    return 0;
}

void add()
{

}
// this produces warning that the function was declared before it existed
// remember, the code runs line-by-line
```
- we can avoid this by using function prototypes
```c
#include <stdio.h>

void add();

int main()
{
    add();
    return 0;
}

void add()
{

}
// now you won't get errors since at compile-time it already knows that it exists
```
```c
// same as
#include <stdio.h>

void add()
{

}

int main()
{
    add();
    return 0;
}
// still no warning, function was defined before invoked
```
