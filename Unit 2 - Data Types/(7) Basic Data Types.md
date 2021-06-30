# Basic Data Types

## Overview

* C has many types of variables and each type is used for storing some kind of data
  * that store integers
  * that store *nonintegral* numerical values (ex: scientific notation, booleans)
  * that store characters
* some examples of basic data types are:
    1. `int`
    2. `float`
    3. `double`
    4. `char`
    5. `_Bool`
* the difference between the types is the memory they occupy and the range of values
  * amount of storage allocated to store a type of data
  * depends of the computer running the program (machine-dependent)
  * an integer might take up 32 bits (4 bytes) or 64 bits (8 bytes)

## `int`

* a data type that stores integral values only (cannot contain decimal places)

    ```c
    int number = 2; // correct
    int num = 2.3; // wrong
    ```

* a minus sign `-` preceding the number indicates that the value is negative (`int num = -3`)
* `int` is a signed integer, meaning it can be positive, negative, or zero
* if it's preceded by `0x`/`0X`, the value is taken in hexadecimal notation (base 16) (`int rgbColor = 0xFFEF0D`)
* no embedded spaces are permitted between the digits, for example `12 000` is not allowed
* vals larger than 999 cannot have commas (`12,000` needs to be written as `12000`)

## `float`

* for storing floating-point numbers (decimals)
* values `3.`, `125.8`, and `-.001` are valid
* floats can also be in scientific notation
  * `1.7e4` represents the value `1.7 * 10 ** 4`

```c
float decimal = 4.555;
```

## `double`

* same as `float`, only with roguhly twice the precision
  * used whenever the `float` var range is not enough
  * can store twice as many significant digits
  * most computers have `double` values using 64 bits
  * all floats are expressed as doubles in the C compiler
  * to explicitly express a float, append an `f`/`F` to end of the number (ex. `12.5f`)

```c
double Factor = 22.442e2
```

## `_Bool`

* used to store `0` or `1`, used for indicating yes/no, on/off, or true/false (binary)
* used in programs that need to have a Boolean condition, for example: checking whether all data has been read from a file by indicating `0` or `1`
* `0` is for a false value; `1` is for a true value

```c
_Bool t = 1;

// this is the same as

#include <stdbool.h>
bool boolVar = true;
```

* Note: the use of `bool`, `true` and `false` is fine, but you have to include the `stdbool` header file. Otherwise, C will not treat them as reserved, and you can only use `_Bool`, `1` and `0`.

## Other Data Types

* C offers many other integer types
  * integer types vary in range of vals offered in whether negative numbers can be used
* C has three adjective keywords to modify basic integer type, and can also be used by itself
    1. `short`
        * uses less memory than `int` and can save memory when program is large
    2. `long`
        * takes more memory than `int` and is used to express larger integers
    3. `long long`
        * uses more memory than `long`
        * a constant of type `long` can be turned to `long long` by appending `l` or `L` to the end of integer

        ```c
        long int number = 131071100L;
        ```

    4. `unsigned`
        * only does positive values
        * cannot have negative numbers
    5. `signed`
        * accepts positive and negative numbers
        * used with any signed types to make it explicit
* type specifiers can also be added to `double`
  * `long double` are written as float constant with letter l or L following the double

```c
long double US_deficit;
```

* basically, these are all the same:

```c
short
short int
signed short
signed short int
```
