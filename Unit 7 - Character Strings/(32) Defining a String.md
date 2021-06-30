# Character Strings

- C has no special var type for strings
  - there are no special oper. for processing strings
  - however, stdlib has a range of functions for strings
- strings are stored in `char` array
  - one character per one memory cell
- to decleare, use `char` and `[]` to indicate size

```c
char Hello[20];
```

- this variable can hold up to 19 char
  - extra null character

# Initializing a String

- you can initialize when declaring

```c
char Hello[] = {'H', 'e', 'l', 'l', 'o', '!'};
```

- initialization is same as any other
- ***Note*** that it's fine to not declare the array size of any type so long as it's initialized, C infers the array size from there (incl. null char) <br/> <br/>
- you can initialize part of an array with a string

```c
char str[40] = "To be";
```

- compiler initializes first five elements with characters shown; `str[0]` is T, `str[4]` is e
- `str[5]` is `\0`, and space is allocated for all 40 elements

## Errors

- you can specify string size explicitly, just make sure to leave space for null
- if size is too small for string, compiler won't put the null character, and won't raise an error (somehow)

# Assigning Values after Initializing

- you can't assign arrays to other arrays in C

```c
char s[100]; // declare
s = "hello"; // initialize, won't work ('lvalue required')
```

- performing an assignment operation on an entire string requires `strncpy()`
  - function in stdlib that assigns value of char array after declared or initialized
- u still can assign it element by element tho

# Displaying a String

- when referring to string in array, use name by itself
- to display string, use `%s` in `printf()`

# Inputting a String

- to input, use `scanf()`
- `%s` is used as format specifier
- no need to put `&` (address-of oper.) on string
- `scanf()` will **not** get all characters, rather the input *stops* after a space.
  - better replacements are `gets()` and `fgets()`

# Testing if two strings are equal

- you can't test if two strings are equal with a normal `==` oper.
- `==` also won't work on structs and arrays
- to determine if two strings are equal, compare the strings character by character
  - you can use `strcmp()` for this

## **Reminder**

```c
"x" /* is not the same as */ 'x'

'x' 
// basic type, char

"x" 
// derived type, array of char
// really just 'x' and '\0'
```
