# Initialization

- you'll want to assign initial values for elements most of the time
- defining initial values makes it easier to detect errors
- you can assign initial values to arrays at declaration
- to initialize, provide values in a list
  - separated by commas `,` and enclosed in braces `{}`

```c
int counters[5] = { 0, 0, 0, 0, 0 };
// this initializes each of the 5 elements to 0

int integers[5] = { 0, 1, 2, 3, 4 };
// this sets integers[0] to 0, integers[1] to 1, and so on
```

## Is it necessary to initialize an entire array? **No.**

- it's not necessary to completely initialize an entire array
- if fewer values are specified, remaining values are set to 0

```c
float sampleData[500] = { 100.0, 200.5, 695.6 };
// initializes first three values to 100.0, 200.5, and 695.6 and sets remaining 497 elements to 0.000...
```

# Designated Initializers

- in C99, designated initializers feature was added
- this allows you to choose which elements are initialized
- enclose element number in a pair of brackets

```c
float sampleData[500] { [2] = 500.5, [1] = 300.0, [0] = 100.0 }
/* 
element 0 is 100.0
element 1 is 300.0
element 2 is 500.5
element 3, 4, ... is 0.00...
*/
```

# Initializing all elements to same value

- there is no built-in function in C to initialize all elements to one value
- instead, you'd have to make a loop for this

## Example

```c
#include <stdio.h>
#include <stdlib.h>
int main ()
{
    int squareValues[10] = { 0, 1, 4, 9, 16 }; // 0^0 = 0, 1^1 = 1, so on...
    int i;
    
    // when i = 5, it's on the SIXTH value already
    // i must be less than 10, because the TENTH value is squareValues[9]
    for ( i = 5; i < 10; ++i )
        squareValues[i] = i * i;
    
    // same mechanics, except i is the first element of the array [0]
    // prints the position and value
    for ( i = 0; i < 10; ++i )
        printf("squareValues[%d] \t %d\n", i, squareValues[i]);

    return 0;
}
```

```txt
squareValues[0]          0
squareValues[1]          1
squareValues[2]          4
squareValues[3]          9
squareValues[4]          16
squareValues[5]          25
squareValues[6]          36
squareValues[7]          49
squareValues[8]          64
squareValues[9]          81
```
