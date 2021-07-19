# Concept of Structures

- structures are like powerful arrays
    - it's like using objects in object-oriented languages
    - the difference is structures can't use methods
- allow the coder to group attributes of a given variable

```c
// say you want to store a date inside a program
int month = 9, day = 25, year = 2015;
```

- suppose program also needs to store date of purchase of an item
    - you have to make multiple variables repeatedly to store (lots of variables)
    - these variables are related in logic and should be grouped together
- it's better to group sets of variables together

# Creating Structure

- struct declaration describes how a structure if put together
    - like a blueprint

- use `struct` keyword to define colelction of variables of various types
    - treated as a single unit

```c
struct date 
{
  int month;
  int day;
  int year;
};
```

- there is no memory allocation for this declaration
    - it just tells the compiler that this thing exists
- `month`, `day`, and `year` are called members or fields
    - members of structure appear between the braces

# Using a Structure

- definition of `date` defines a new data type
    - variables can now be declared of type `struct date`
- kind of like `enum` except that an `enum` can only hold one value

```c
struct date today;
```

- above statement declares variable to be type `struct date`
    - memory is now allocated for variables above
    - means that three integer memory blocks are allocated

# Accessing Members

- struct variable name is not a pointer
    - there's a special syntax for accessing members
- refer to member of structure by writing variable name followed by period then member variable name
    - period `.` is known as dot operator or member selection operator
    - you can't have spaces between variable name, period, and member name

## Example

- to set value of the day of `struct date today` day to 25 and year to 2015, write

```c
today.day = 25;
today.year = 2015;
```

- testing the value of month

```c
if (today.month == 12) printf("today.month is December.");
```

# Full Example

```c
#include <stdio.h>
#include <stdlib.h>

struct date {
    int month;
    int day;
    int year;
};

int main(void) {
    struct date today;

    today.month = 7;
    today.day = 13;
    today.year = 2021;

    printf("Today is %d/%d/%d\n", today.month, today.day, today.year % 100);
}
```

```txt
Today is 7/13/21
```

# Structures in Expressions

- structure members follow same rules as ordinary variables

```c
// #include <math.h>
century = trunc(today.year / 100) + 1;
```

# Defining Structure & Variable Simultaneously

- it's valid to declare variable to be of a structure type at declaration time
    - you can include variable name before terminating semicolon of definition
    - you can assign initial values to variables

```c
struct date
{
    int month;
    int day;
    int year;
} today;
// today is a variable of type struct date
```

> **Tip:** just like in other types, you can use `typedef` to make an alias of that type. by using this, you can omit `struct date`

```c
typedef struct date {
    int month;
    int day;
    int year;
} date;

void main(void) {
    date today;
    today.day = 7;
    today.month = 7;
    today.year = 1515;

    printf("Date is %d/%d, %d", today.month, today.day, today.year);
}
```

## Unnamed Structures

- you also have the ability to omit tag name (the type after `struct`)
    - if all variables of a structure type are defined when structure is defined, name can be omitted

```c
struct
{               // declaration
    int month;
    int day;
    int year;
} today;        // structure variable declaration
```

- disadvantage is that `today` will be the only instance of this structure
    - all variables of this structure type must be defined in that same statement

# Initializing Structures

- similar to initializing arrays
- elements are inside pair of braces
    - each element is separated by a comma

```c
struct date today = {7, 13, 2021}; // month = 7, day = 13, year = 2021
```

- you can also initialize only some values just like arrays
    - the rest of the values are 0

```c
struct date today = {7, 13}; // no year, year = 0
```

- you can also specify member names in list
    - you can initialize members in any order, or specify members to be initialized

```c
struct date today = {
    .year = 2021,
    .day = 13
}; // no month
```

## Assignment with Compound Literals (*Not Initialization*)

- you can assign one or more values to structure in single statement with compound literals

```c
struct date today = {7, 6, 2021};
printf("Date is %d, %d, %d", today.month, today.day, today.year);

today = (struct date) {7, 7, 2021};
printf("Date is %d, %d, %d", today.month, today.day, today.year);
```

- statement can appear anywhere in the program because it's an assignment operation
    - type cast operator tells compiler the new type of the expression
    - list of values after cast are assigned to members of structure in order
    - listed in same way as if initializing structure variable
