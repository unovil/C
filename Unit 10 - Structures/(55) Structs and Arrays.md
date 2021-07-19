# Arrays of Structures

- structures are useful to logically group elements together
    - for example, it's necessary to keep track of 1 (and not 3) variables for a date
    - to handle 10 dates, you need to keep track of 10 (and not 30) variables
- it's also useful to group these into arrays to keep track of 1 (and not 10) variables
    - it's fine to define an array of structures

## Declaring Array of Structures

```c
struct date myDates[10];
```

- defines array called `myDates`, consists of 10 elements
    - each element in array is type `struct date`

## Referencing a Structure Element in an Array

- for example, say you want to set second date inside `MyDates` to January 1, 1900

```c
myDates[1].month = 1;
myDates[1].day = 8;
myDates[1].year = 1900;
```

## Initializing Array of Structures

- similar to initialization of multidimensional arrays

```c
struct date myDates[5] = {
    {12, 10, 1975},
    {12, 30, 1980},
    { 8, 25, 2007}
};
```

- the braces are optional, though recommended

```c
struct date myDates[5] = { 12, 10, 1975, 12, 30, 1980, 8, 25, 2007}; // hard to read
```

- initialize the third element to a specified value

```c
struct date myDates[5] = { [2] = {12, 10, 1975} };
```

- sets month and day only

```c
struct date myDates[5] = { [1].month = 12, [1].day = 30 };
```

# Structures of Arrays

- also possible to define structures that contain arrays as members
    - most common use is to set up array of characters in structure

```c
// say you want to define structure called month info
// numberOfDays is the number of days of the month
// name is the 3-char abbreviation of the month
typeset struct monthInfo {
    int numberOfDays;
    char name[3];
} monthInfo;
```

## Referening Structures of Arrays

```c
monthInfo january;
january.numberOfDays = 31;
january.name = "Jan";

// can also be

january.name[0] = 'J';
january.name[1] = 'a';
january.name[2] = 'n';
```

## Initializing Structures of Arrays

```c
monthInfo february = { 28, {'F', 'e', 'b'} };
```

## Set up an Array of Structures of Arrays

```c
monthInfo theMonths[12];
```
