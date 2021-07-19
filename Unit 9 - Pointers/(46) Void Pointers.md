# Flexibility of Void Pointers

- `void` type means the absence of a type
- pointer of type `void*` can contain address of any data type
    - very flexible

- `void*` is used as param or return type with type-independent functions

- any kind of pointer can passed as `void*`
    - void pointer won't know the type of object it's pointing to
        - cannot be dereferenced directly
    - void pointer should first be cast to another pointer type to be dereferenced

```c
int v = 5;
void *pv = &v;

printf("value at v is %d", *(int*) pv);
// (int*) pv to cast pv to int pointer
// then add * prefix to dereference casted pointer
```

```txt
value at v is 5
```
