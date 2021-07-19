# Adding an Integer to a Pointer

```c
#include <stdio.h>
#include <string.h>

void main(void) {
    char str[] = "hi hello";
    char *pstr = str;

    for (int i = 0; i < strlen(str); ++i) {
        printf("str[%d] = %c  |  ", i, str[i]);
        // str[0] = t, str[1] = h, ...
        printf("*(pstr + %d) = %c  |  ", i, *(pstr + i));
        // *(pstr + 0) = t, *(pstr + 1) = h, ...
        printf("&str[%d] = %p  |  ", i, &str[i]);
        // address of every element in str
        printf("pstr+%d = %p\n", i, pstr + i);
        // address of every element by incrementing pstr
    }
}
```

```txt
str[0] = h  |  *(pstr + 0) = h  |  &str[0] = 0xffffcbe7  |  pstr+0 = 0xffffcbe7
str[1] = i  |  *(pstr + 1) = i  |  &str[1] = 0xffffcbe8  |  pstr+1 = 0xffffcbe8
str[2] =    |  *(pstr + 2) =    |  &str[2] = 0xffffcbe9  |  pstr+2 = 0xffffcbe9
str[3] = h  |  *(pstr + 3) = h  |  &str[3] = 0xffffcbea  |  pstr+3 = 0xffffcbea
str[4] = e  |  *(pstr + 4) = e  |  &str[4] = 0xffffcbeb  |  pstr+4 = 0xffffcbeb
str[5] = l  |  *(pstr + 5) = l  |  &str[5] = 0xffffcbec  |  pstr+5 = 0xffffcbec
str[6] = l  |  *(pstr + 6) = l  |  &str[6] = 0xffffcbed  |  pstr+6 = 0xffffcbed
str[7] = o  |  *(pstr + 7) = o  |  &str[7] = 0xffffcbee  |  pstr+7 = 0xffffcbee
```

# hello

```c
#include <stdio.h>

typedef unsigned long long ull;
typedef unsigned long ul;

int main (void) {
    long multiples[] = {15L, 25L, 35L, 45L};
    long *p = multiples;

    for (int i = 0; i < sizeof(multiples)/sizeof(*multiples); ++i) {
        printf("address p + %d (&multiple[%d]): %ld  |  ", i, i, (ul) (p + i));
        printf("*(p + %d) value: %ld\n", i, *(p + i));
    }
    
    printf("\n-> Type long occupies %d bytes\n", (int) sizeof(long));
    return 0;
}
```

```txt
address p + 0 (&multiple[0]): 4294953952  |  *(p + 0) value: 15
address p + 1 (&multiple[1]): 4294953960  |  *(p + 1) value: 25
address p + 2 (&multiple[2]): 4294953968  |  *(p + 2) value: 35
address p + 3 (&multiple[3]): 4294953976  |  *(p + 3) value: 45

-> Type long occupies 8 bytes
```
