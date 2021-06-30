# Switch

- conditional operator and the if-else statements make it easy to write programs that choose between two alternatives
- many times though, a program needs to choose one of several alternatives
  - can be done with else if, else if, etc.
  - prone to errors
- when value of variable is successively compared against different values, use this

## Syntax

```c
switch (expression)
{
    case value1: //if
        program statement
        ...
        break;
    case value2: //else if
        program statement
        ...
        break;
    case valuen: //else if
        program statement
        ...
        break;
    default: //else
        program statement
        ...
        break;
}
```

- expression in  `switch` is compared against `value1`, `value2`, and so on
- cases must be simple constants only or constant expressions
- when more than one statement is included, no need to put braces
- `break` is the end of particular case and terminates execution of `switch`
  - forgetting to do this will let program continue to next case
- special (optional) case is `default`; executed if value or expression doesn't match ANY of cases
  - same as `else`

## Example

```c
#include <stdio.h>
enum Weekday {M, T, W, TH, F};
enum Weekday today = M;
switch (today)
{
    case Sunday:
        printf("Today is Sunday");
        break;
    case Monday:
        printf("Today is Monday");
        break;
    case Tuesday:
        printf("Today is Tuesday");
        break;
    default:
        printf("Today is either TH or F");
        break;
}
```

# goto

- has two parts

1. goto
2. label

- label is named following convention in naming variable
- when the `goto` is encountered, the execution jumps to the `label` and continues from there
- usually not used, and also very outdated
