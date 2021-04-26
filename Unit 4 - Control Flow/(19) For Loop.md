# Repeating Code
- repeat a block of statements
    1. until a condition is met, or
    2. a specific number of times
- repeating code without condition is infinite loop
- number of times loop is repeated is controlled by count (counter-controlled)
# For Loop
- execute block of statements a number of times
## General Syntax
```c
for ( starting_condition; continuation_condition; action_per_iteration)
{
    loop_statement1;
    loop_statement2;
    .
    .
    .
}
```
`starting_condition`
- usually sets initial value to loop control variable
- can also declare and initialize variables of same type with declarations
- variables are local to loop and will be discarded when loop ends

`continuation_condition`
- logical expression (evals to true or false)
- as long as condition is true, loop continues
- typically checks value of loop control variable
- tested at beginning of each iteration rather than end
    - `loop_statement` will not execute if `continuation_condition` starts as false

`action_per_iteration`
- executed at end of each iteration
- usually increment or decrement one or more loop control variables
- can modify several variables, just put commas to separate

## Example
```c
#include <stdio.h>

for (int i = 1, j = 2; i <= 5; ++i, j += 2)
{
    printf("%5d", i*j)
}
```
# Infinite Loop
- YOU ARE NOT OBLIGATED TO PUT ANY PARAMETERS
```c
for ( ; ; )
{
    printf("Hello!\n");
}
```
- this will print `Hello!` forever