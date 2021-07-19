# Power of Pointer Arithmetic

- using pointers to array comes into play when sequencing through elements of array

```c
int arr[100] = {2, 5, 4, 3, 2};
int *parr = arr;              // used to access first elem of arr
```

- to reference `arr[3]` through `parr`, add `3` and apply indirection oper

```c
printf("%d\n", *(arr + 3)); // gets 3, the 4th element of arr
```

## Pointing to Specific Location in Array

- formula `*(parr + i)` is used to access value in `arr[i]`
- to set `arr[10]` to `30` you could do

```c
int element = 10;

arr[element] = 30
// or using a pointer
*(parr + element) = 30;
```

## Shifting Through an Array

- to set `parr` to point to nth element of `arr`, apply address operator to `values[0]` and simply increment/decrement to move through

```c
element = 1;

parr = &values[0 + element];
// or
parr++; // assuming parr = values or &values[0]

// you can also decrement to go back
parr--; // goes back to &parr[0]
```

## Example

### Array notation

```c
#include <stdio.h>
#include <stddef.h>

int arrSum(int array[], const int size);

void main()
{
    int someArr[10] = {0, 3, 5, 7, 4, 6, 8, 2, 1, 9};

    printf("The sum of someArr is %d\n", arrSum(someArr, 10));
}

int arrSum(int array[], const int size)
{
    int sum = 0, *parray;
    int *const arrayEnd = array + size; 
    // for example, there are 10 members in the array
    // to get to the last member, simply add 10 to &array[0]
    // const stops arrayEnd from mistakingly change value of an element

    for (parray = array; parray < arrayEnd; ++parray) sum += *parray;
    // for address of every member in the array, dereference and add to sum

    return sum;
}
```

```txt
The sum of someArr is 45
```

- to pass array to function, only specify name of array
- to produce pointer to array, you need to specify name of array

- **implies** that in `arrSum()`, what was passed was actually a pointer to array values
    - it explains why you can change elements of array in a function
    - you are indirectly changing the array elements

- so why is the argument of the function not a pointer?
    - well, it could be

  ```c
  int arrSum(int *array, const int size);
  ```

    - perfectly valid
        - pointers and arrays are related
        - you can declare array to be "array of ints" inside `arrSum()` or "pointer to int"

- if you're using indexes to reference elements of array passed, declare the argument to be array
    - clearer and better reflects use of array by function

- if you're using argument as pointer to array, declare it to be a pointer

### Pointer notation

```c
#include <stdio.h>
#include <stddef.h>

int arrSum(int array[], const int size);

void main()
{
    int someArr[10] = {0, 3, 5, 7, 4, 6, 8, 2, 1, 9};

    printf("The sum of someArr is %d\n", arrSum(someArr, 10));
}

int arrSum(int *array, const int size)
{
    int sum = 0;
    int *const arrayEnd = array + size; 

    // for ( ; array < arrayEnd; ++array) sum += *array;
    while (array < arrayEnd) {sum += *array; ++array}
    
    return sum;
}
```

# Summary

```c
int urn[3];
int *ptr1, *ptr2;
```

|        Valid       |        Invalid        |                Reason                |
|:------------------:|:---------------------:|:------------------------------------:|
| `ptr1++;`          | `urn++;`              | You can't increment arrays           |
| `ptr2 = ptr1 + 2;` | `ptr2 = ptr2 + ptr1;` | You can't add two pointers together  |
| `ptr2 = urn + 1;`  | `ptr2 = urn * ptr1;`  | You can't multiply pointers together |

- functions processing arrays use pointer to arrays as args
- you can choose between array and pointer notation for array-processing functions
- using array notation makes function more obvious working with arrays
    - has more familiar look to coders of FORTRAN, Pascal, Modula-2, or BASIC
- others can be more versed to use pointers and find pointer notation natural
    - closer to machine language and leads to more efficient code
