# Local Variables

- variables inside function are **automatic local variables**
  - automatically initialized each time function is called
  - values are *local* to function; after function ends, all memory within function (such as values) are discarded
- value of local variable can only be accessed by function which variable is defined
  - cannot be accessed by any **other** function
- if a value is already assigned to a variable inside function, that value is assigned each time function is called
  - you can use the `static` keyword before data type so that the variable with that type is remembered even when the function is over
  - still can't be accessible outside the function though

```c
void something()
{
    static int counter = 0;
    counter++;

    printf("Counter is %d\n", counter);
}

int main()
{
    something(); // prints 1
    something(); // prints 2, since counter is static and thus remembered by C
}
```

- local variables are also applicated to any code block where variable is created (like loops, if statements, etc.)

# Global Variables

- opposite of local; accessed by any function in program
- declared outside of any function (including main)
  - does not belong to any function
- any function in program can change value of global variable
- if a local variable is declared in function with same name, local variable takes precedence
  - global is not accessible and prevented from being accessed normally

# Example

```c
int globalVar = 0;

void Function() {
    int x; // local
    // can access globalVar and x
}

int main() {
    int localMain = 0; // local
    // can access globalVar and localMain
    return 0;
}
```

# Avoid Globals

- in general, global variables are bad and should be avoided
  - promotes coupling (dependency) between functions
    - when many functions use a global variable, these functions may depend on each other
  - hard to find bug location
  - hard to fix bug once found
- use parameters in functions instead
  - if there's a lot of data, use a structure `struct` (haven't been talked about yet)
