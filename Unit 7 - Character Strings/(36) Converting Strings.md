# Converting Strings

- very common to convert character cases of string

- both `toupper()` and `tolower()` return eithre coverted char or same char for chars that don't use cases

Example:

```c
#include <stdio.h>
#include <ctype.h> // need this lib for toupper and tolower

int main(void) {

    char buff[20];

    gets(buff);

    for (int i = 0; ; ++i)

        // toupper and tolower return an int 
        // that can be casted to char
        /* checks if new character is \0 (if so, it breaks) */
        if ( ( buff[i] = (char) toupper(buff[i]) ) == '\0')
            break;

    printf("%s", buff);
    return 0;
}
```

## Converting Strings to Numbers

- `stdlib.h` has functions for converting string to numeric values

<img
  src = "../pictures/converting string to numeric.png"
  alt = "Converting String to Numeric"
  style = "display: block; margin-left: auto; margin-right: auto">

- `atof()` also has some other features
    - it returns `Infinity` as the double if strings `INF` or `INFINITY` is passed (case insensitive)
    - it returns `not a number` from string `NAN` (case insensitive)

- this should only be used for strings that can be called numbers (like `"98.4"` and `"100"`)
