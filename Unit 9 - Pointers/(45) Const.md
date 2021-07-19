# Overview

- `const` modifier is used on variable or array
    - contents of variable/array cannot be changed

- with pointers, we consider 2 things
    - whether pointer will be changed
    - whether value that pointer points to is changed

## Constant Address Values

### workaround of the const

```c
long v = 99L;
const long *pv = &v; // defines pointer to a constant
```

- declared that value pointed to by `pv` is constant
    - this means that `pv` can't be a way to change the value of `v`
    - you can still do this though

  ```c
  v = 100L; // fine by the compiler
  *pv = 200L; // error
  ```

### undefined behavior

- also happens when

```c
const long v = 99L;
long *pv = &v;
*pv = 100L; // valid, but undefined behavior since v should be constant
```

### you can still modify the address itself

- you can still modify the value of a pointer (its address)

```c
int n = 20;
int m = 30;
const int *pn = &n;

pn = &m; 
// perfectly fine since you didn't alter the value at the address
// you just altered the address itself
```

- you still can't change the value at the new address

## Constant Pointer Values

- you might also want to make sure that address in a pointer won't change

```c
int count = 43;
int *const pcount = &count; // define constant pointer
```

### you can still change value at address

- this is fine

```c
*pcount = 45; // very much fine
```

### but you can't change the address

- this is not fine, if you do this please get help

```c
int number = 90;
pcount = &number; // error!
```

## Lots of `const`

- you can create a constant pointer that points to constant value

```c
int item = 25;
const int *const pitem = &item;
// noe u can't change the value of item through pitem
// noe u also can't change the address
```

### making sure it's everlasting

- if you want to make sure nobody changes the variable itself

```c
const int item = 25;
const int *const pitem = &item;
// noe u can't change item itself
```
