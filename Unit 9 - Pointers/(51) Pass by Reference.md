# Overview

- there are a few ways to pass data to function
    - pass by value
    - pass by reference

- C passes by value on default, the language can't pass by reference
    - instead, it simulates passing by reference by copying addresses

- others can pass by reference, like mainstream languages
    - Python, Java, C#, Ruby, JavaScript, and PHP

# Pass by Value

- function copies the value of an argument into parameter of function
    - the changes made to the argument have no effect
    - because it's just a replica

- C uses call by value to pass arguments
    - code in the function can't alter arguments in the function
    - there are no changes in values outside the function (though it has been changed inside)

## Example

```c
/* function to swap values */
void swap (int x, int y) {
  int temp;

  temp = x; // put value of x somewhere for now
  x = y;    // put value of y into an empty container x
  y = temp; // now put the backup value x into container y
}

int main() {
  int a = 100;
  int b = 200;

  printf("a was %d  |  b was %d\n", a, b);
  swap (a, b);
  printf("a is  %d  |  b is  %d\n", a, b);

  return 0;
}
```

```txt
a was 100  |  b was 200
a is  100  |  b is  200
```

# Pass By Value But This Time It's Copies of Pointers 😲

- functions and pointers get along
    - you can pass pointer as argument to function
    - also have function return pointer
- function copies address of argument in parameter
    - address is used to access the actual argument in call (indirectly)
    - changes made to address reflect changes to passed argument
- this happens because there's only every place in memory has unique address
    - making copies of the same address won't matter since all point to one place
    - therefore, you can use all of those copies to change the value at that place
- no need for global variables!

## How to Use?

- to pass value by reference, argument pointers are passed like any other value
    - declare function parameters as pointer types
    - changes in function are reflected, unlike with call by value

```c
// function to swap values stored at two int pointers
void swap_Pointers (int *x, int *y) {
    int temp;

    temp = *x; // put value in address of x somwhere
    *x = *y;   // put value in address of y into empty container in address x
    *y = temp; // put backup value in address x into value at address y
}

int main() {
    int a = 100;
    int b = 200;

    printf("a was %d  |  b was %d\n", a, b);
    swap_Pointers (&a, &b);
    printf("a is  %d  |  b is  %d\n", a, b);

    return 0;
}
```

```txt
a was 100  |  b was 200
a is  200  |  b is  100
```

## Const Pointer Parameters

- you can make a function paramater `const`
    - function will treat argument passed for this parameter as constant
    - useful when parameter is a pointer

- apply `const` to pointer parameter to specify that function won't change the value that an argument points to

```c
bool sendmessage(const char* pmessage)
{
  // code to send message
  return true;
}
```

- `pmessage` is a pointer to a `const char`
    - it's the `char` value that's `const`, not the address
- you can make the pointer constant too
    - but, it makes little sense because you can't change the address it has

# Returning Pointers

- returning pointer from function is a useful feature of C
    - provides a way to return a whole set of values
- you have to declare a function that returns a pointer

```c
#include <stdio.h>
#include <stdlib.h>

int * tenMultiples(const int step) {
  static int r[10];
  
  for (int i = 0; i < 10; ++i) {
    r[i] = 10 * (i + 1);
  }

  return r;
}

int main() {
  int *list;
  int multiples = 12;

  list = tenMultiples(multiples);

  for (int i = 0; i < 10; ++i)
    printf("*(list + [%d]) : %d\n", i, *(list + i));

  return 0;
}
```

```txt
*(list + [0]) : 10
*(list + [1]) : 20
*(list + [2]) : 30
*(list + [3]) : 40
*(list + [4]) : 50
*(list + [5]) : 60
*(list + [6]) : 70
*(list + [7]) : 80
*(list + [8]) : 90
*(list + [9]) : 100
```

- be careful, there are hazards to returning a pointer
    - it's not a good idea to return address of local variable outside function

  ```c
  int myFunction () {
    int something[10];

    return something;
    // not a good idea
  }
  ```
  
    - define the local variable as `static` instead
  