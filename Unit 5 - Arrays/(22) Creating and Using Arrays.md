# Overview

- it's very common to store many data values of a specified type in a program
  - for example, if you want to store 200 scores of a game
  - you'd need 200 variables, which is tiresome
  - instead, you could use an array
- arrays can group values together under a single variable
  - no need to separate variables
- Limitations:
    1. once an array is made, the number of things in that array (it's size) cannot be changed
    2. all the items in that array need to be of the same data type

# Declaring Arrays

- data items in array are known as 'elements'
- elements in array cannot be of same type (`int`, `long`, etc.)
  - for example, you can't have a single array made of `int`s and `double`s
- declaring an array is similar to a normal variable with single value
  - the only difference is to put a number between square brackets `[]` following name
- number put is the size of the array
  - known as size of array or **array dimension**

Example:

```c
int List[10];
// make an array named "List" that has 10 elements of data type int
```

# Accessing Array Elements

- each data item in array is accessed by same name (name of array itself)
- select an element by using index value between square brackets following array name
- index values are 0-based
  - the first item is 0, the second is 1, and so on
  - in an array of 10, the last element has a value of 9
- it's very common to mistake that arrays start from 1
  - known as off-by-one error
- use integer to explicitly reference element you want to access
  - to access fourth value, use `arrayName[3]`
- very common to use loop to access each element

```c
for ( i = 0; i < 10; ++i)
    printf("Number is %d", numbers[i]);
// for every number in "numbers" (0th-9th), print that statement
```

# Errors

## Array out of Bounds

- if the index value you're using is outside the range of the array, program can crash ORRR it "may" work normally, but really doesn't
- make sure!!!

# Assigning values to Array

- value can be stored in element of array by specifying array element on left side of equal sign

```c
grades[100] = 95;
```

- you can also use variables to assign values to array
