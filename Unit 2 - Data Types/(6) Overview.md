# Overview

* a program needs to store instructions of the program and data it acts upon while computer executes program
  * info is stored in RAM
  * RAM (*random access memory*) contents are lost upon shut down
  * hard drive stores concrete data
* think of RAM as an ordered sequence of boxes
  * box is full when it is `1` and it's empty when it's `0`
  * each box has a binary digit, `0` or `1` (`false` or `true`)
  * each box is known as a *bit*
* bits are divided into eight (called a *byte*)
  * each byte has a label with a number (known as the *address*)
  * each address uniquely references a certain byte in the RAM.

## Variables

* **constants** are data that do not change and retain their values throughout the program
* **variables** are data that can change as the program runs
  * vars are the names you give to comp. memory loc. which are used to store values in the program

For example, assume you want to store two values `10` and `20`

* create two variables with meaningful names, like `age1` and `age2`
* store the values in the two variables
* retrieve and use the stored values

## Naming Variables

* all names must begin with a letter `a-z` or underscore `_` and can be followed by any letters, underscores, or digits `0-9`

```c
// Correct
int Uno;
int myFlag;
int _data123;
int _someVariable;
int _0x0002304923490234; // this is syntactically correct, though it's not meaningful

// Wrong
int 120312; // just numbers
int 1as; // begins with a number
int someVariable%; //% not allowed
int \n%$; // \, %, and $ not allowed
int my Flag; // there's a space
int int; // int is a reserved word and cannot be used as variable name
```

* use meaningful names to increase the readability of the program

## Data Types

* some types of data are **numbers, letters, or words**, and the computer needs to identify and use these different kinds
* a *data type* represents a type of the data which you can process using the program
  * examples are `int float double` etc.
  * also correspond to byte sizes on the program platform
* **primitive** data types are types that are not objects and can store any data
  * C has no objects, so all data types are primitive

## Declaring Variables

* to declare a varibale, you specify the data type, followed by the variable name

    ```c
    type-specifier variable-name;
    ```

---
For example:

* the keyword `int` is to declare the basic integer variable
* type `int` then the name of the variable, then a semicolon `;`

    ```c
    int someNumber;
    ```

---

* to decalre more than one variable, declare each variable separately, or, if all of these have the same data type, you can have a list of variables separated by commas

    ```c
    int num1;
    int num2;
    int num3;

    // or...

    int num1, num2, num3;
    ```

* C requires all variables be declared *before* they're used in the program
* The above code creates variables but doesn't provide values. We can assign values using the `=` operator.

    ```c
    // continuation...

    num1 = 10;
    num2 = 122;
    num3 = 1000;
    ```

## Initializing Variables

* meaning to assign an initial value
* can be done as part of the declaration by following the var name with the assignment operator `=`

    ```c
    int one;
    one = 1;
    // is the same as
    int one = 1;

    int one, two;
    one = 1;
    two = 2;
    // is the same as
    int one = 1, two = 2;

    int one, two = 2
    /* this one is valid, but it
    only initializes 'two', not 'one' */
    ```
