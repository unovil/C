# Structures and Pointers

- pointers to structures are easier to manipulate
- in older implementations, structures can't be passed as arguments to a function, but pointers to structures can
    - even when you pass a structure as argument, pointers are more efficient
- many data representations use structures with pointers to other structures

# Declaring Structure as Pointer

```c
struct date *pDate; // set pDate to NULL
```

- `pDate` is assigned just like other pointers
    - you can set it to point to `todaysDate`

```c
pDate = &todaysDate;
```

- you can (indirectly) access any members of date structure pointed to by `datePtr`

```c
(*pDate).day = 21;
```

- parentheses are **required**!
    - remember operator precedence?
    - struct member `.` has higher precedence than indirection `*`
    - if parentheses weren't there, it would dereference `pDate.day` (which is not a pointer)

# Using Structures as Pointers

- you can dereference `pDate` to check the value

```c
if ((*pDate).month == 12) ...
```

- instead of using `(*<structpointer>)`, use `->`
    - this is the structure pointer operator

so, instead of

```c
(*x).y
```

it's better (and more clearly) expressed as

```c
x->y
```

- so first example can be written as

```c
if (pDate->month == 12) ...
```

## Example of Using Pointer to Structure Operator

```c
typedef struct date {
    int month, day, year;
} date;

int main() {
    date today, *pToday;

    pToday = &today;

    pToday->month = 7;
    pToday->day = 18;
    pToday->year = 2021;

    printf("As of writing, today is %i/%i/%i.\n", 
            pToday->month, 
            pToday->day, 
            pToday->year % 100
    );
    return 0;
}
```

```txt
As of writing, today is 7/18/21.
```

# Structures with Pointers

- pointers can also be a member of a structure

```c
struct pointers {
    int *p1, *p2;
}
```

- you can define a variable of type `struct pointers`

```c
struct pointers pointer;
```

- `pointer` is not a pointer, it's a structure containing two pointers

## Example of Using Structures with Pointers

```c
typedef struct intPointers {
    int *p1, *p2;
} intPointers;

int main(void) {
    intPointers pointergroup;
    int i1 = 100, i2;

    pointergroup.p1 = &i1;
    pointergroup.p2 = &i2;
    *pointergroup.p2 = -99; // now we're not using parentheses since p2 is a pointer

    printf("i1 = %i, *pointers.p1 = %i\n", i1, *pointergroup.p1);
    printf("i2 = %i, *pointers.p2 = %i\n", i2, *pointergroup.p2);
}
```

```txt
i1 = 100, *pointers.p1 = 100
i2 = -99, *pointers.p2 = -99
```

# Character Arrays vs Pointers in Structures

```c
struct names {
    char first[20], last[20];
};

// or?

struct pnames {
    char *first, *last;
};
```

- usually just notational but there are advantages to using character pointers
- there's also a massive difference between the two

For example:

```c
struct names with_array = {"Uno", "Villegas"};
struct pnames with_pointer = {"Teacher", "Uno"};
```

for variable `with_array`

- strings are stored in the structure
- structure allocated 40 bytes to hold two names (1 character = 1 byte)

for variable `with_pointer`

- strings are stored wherever compiler stores string constants
- structure holds two addresses, for a total of 16 bytes
- `struct pnames` allocates nothing for storing strings
- can be used only with strings that have had space allocated elsewhere
    - like string constants or string arrays

**this is the difference.**
pointers in a `pnames` structure should be used to store strings that were already created and allocated somewhere else.

## Using Structures with Character Pointers

- it makes sense to use pointers in a structure to handle a string if it's dynamically allocating the memory
    - you can use a poitner to store the address
    - you can use `malloc()` for getting the right amount of space for the string

# Example of Using Structures with Character Pointers

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

const int SLEN = 25; // string length

typedef struct namect {
    char *fname, *lname;
} namect;

void getInfo (namect *pst) {
    char temp[SLEN];

    printf("Enter your first name.\n");
    fgets(temp, SLEN, stdin);
    temp[strcspn(temp, "\n")] = 0; // removes newline from fgets input

    // allocates dynamic memory to hold first name
    // + 1 for the null terminator
    pst->fname = (char *) malloc(strlen(temp) + 1);

    // copy first name to allocated memory
    strcpy(pst->fname, temp);

    printf("Enter you last name.\n");
    fgets(temp, SLEN, stdin);
    temp[strcspn(temp, "\n")] = 0; // removes newline from fgets input

    // allocates dynamic memory to hold last name
    pst->lname = (char *) malloc(strlen(temp) + 1);

    // copy last name to allocated memory
    strcpy(pst->lname, temp);
}


int main(void) {
    namect employee_name, *pEmployee_name;
    pEmployee_name = &employee_name;

    getInfo(pEmployee_name);

    printf("Your name is %s %s.", pEmployee_name->fname, pEmployee_name->lname);
}
```

```txt
Enter your first name.
Uno
Enter you last name.
Villegas
Your name is Uno Villegas.
```
