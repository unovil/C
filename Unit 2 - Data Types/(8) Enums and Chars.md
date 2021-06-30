# Enums and Chars

## Enums

* allows to define variable and specify valid values that could be stored

### To define

1. type `enum`
2. then name of enumerated data type
3. then lift of identifiers enclosed in braces (these define permissible values that can be assigned)

```c
enum primaryColor {red, yellow, blue};
```

* variables in this data type can also be assigned the values `red`, `yellow`, and `blue` (no other values)

### To use

1. use `enum`
2. followed by the type name
3. followed by variable/s

```c
enum primaryColor myColor, herColor;
```

* these two new variables can only be either one of the three values `red`, `yellow`, and `blue`

```c
myColor = red; //this is fine
herColor = orange; //this produces error
```

### Enums as ints

* compiler treats enumeration identifiers as integer constants, beginning from 0

```c
//                  0     1      2
enum primaryColor {red, yellow, blue};
```

* this means that printing a variable with type `enum` will give an integer.

```c
#include <stdio.h>
#include <stdlib.h>
enum primaryColor myColor = red;
printf("My color is %d\n", myColor);

myColor = yellow;
printf("My color is %d\n", myColor);

myColor = blue;
printf("My color is %d\n", myColor);
```

```txt
My color is 0
My color is 1
My color is 2
```

#### Any way to change the int?

* there is! just use the assignment operator `=` for changing the value
  * unless changed, all values to the right continue the count

```c
//         0    1       10        11
enum dirs {up, down, left = 10, right};
```

## Char

* a single character
  * could be `'a'`, `'6'`, `';'`
* to know if they are, just put single quotes `''` to declare the `char` type
* it's also possible to declare `char` to be `unsigned`
  * it's a bit weird, but it makes more sense when moving to the ASCII characters
  * characters can still be negative or positive digits
* also, not to be confused with character strings (those are sequences of characters, not a single one)

### To declare

1. Keyword `char`
2. use a variable name
3. put single quotes only, make sure that single character used only

```c
char boil; /* declare... */
boil = 'T'; // fine
boil = "T"; // this is a string, NOT char
boil = T; // this is a variable, NOT char
```

* also possible to use numerical codes (ASCII) for assigning values
  * there's a whole standard table of values corresponding to characters

```c
char grade = 65; // fine for ASCII, but poor style
```

## Escape Characters

* C has special chars that can represent actions
  * like backspacing, going to next line, or making the speaker beep
* represent the actions using special symbol sequences called escape sequences
* must be enclosed in single quotes when assigned to character variable

```c
char x = '\n' // this is a newline
```

![Some examples of escape sequences](https://cdn.educba.com/academy/wp-content/uploads/2020/01/Escape-Sequence-is-C.png)
