# While
- repeat set of statements as long as a logical expression is true
```
while this condition is true
    keep doing this
```
## Syntax
```c
while (expression)
    statement;

// or

while (expression)
{
    statement1;
    statement2;
    ...
}
```
- `expression` is tested at start of loop
    - if it starts out false, no statements are executed
- if `expression` starts as true, while loop must have mechanism to make this false after a certain amount of iterations
    - otherwise you get infinite loop
## Example
Counter Controlled
- this has a set number of iterations
- so long as you don't change the code, the count is always the same
```c
#include <stdio.h>

int main (void)
{
    int count = 1;

    while ( count <= 5 )
    {
        printf("%i\n", count);
        ++count;
        // these statements continue until count is 5, then ends after
    }
}
```

Logic Controlled
- the numebr of iterations vary (according to logic)
- even by not changing code, count can be different each time
```c
#include <stdio.h>

int main (void)
{
    int num = 0;
    scanf ("%d", &num);

    while (num != -1)
    {
        scanf("%d", &num);
        // basically a guessing game
    }
}
```

# Do...while
- in a while loop, body executes while condition is true

- do-while loop executes body for first time unconditionally
    - guaranteed to execute at least once
    - condition is at bottom
- after initial execution, body executes while condition is true (like normal)
```c
do
{
    statement1;
    statement2;
    ...
}
while (expression);
```
## Examples
Counter controlled
```c
int number = 0;

do
{
    number++;
}
while (number < 4);
```

Logic Controlled
```c
do
    scanf("%d", &number);
while (number != 20);
```

# Which loop to use?
1. Decide whether you need pre or post loop
    - usually will be pre test loop (`for` or `while`)
    - better to look before you "loop" (eehhehehehe)
    - easier to read is loop test is found at beginning
    - important usually that loop be skipped if test is not initially met
2. It's a matter of taste in switching between `for` and `while`
    - you can omit first and third expressions for the `for` parameters to make it a `while` loop
        ```c
        for (;test;)

        // is the same as

        while (test)
        ```
    - prefacing an initialization and including updates to `while` will make it like `for`
        ```c
        initialization_statement; // like int x;
        while (test)
        {
            body_statements; // perhaps printf("x is %d", x)
            update; // possibly x++
        }

        // same as

        for (initialization; test; update)
            body;