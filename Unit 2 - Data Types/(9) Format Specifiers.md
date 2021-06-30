# Format Specifiers

* displays variables as output
  * specify which type of data is displayed
* start with a % symbol

```c
int sum = 89;
printf("The sum is %d\n", sum);
```

## printf()

* has two items or arguments within ()
  * separated by comma
* first argument is always char string to display
  * you might also want to have value of certain program variables displayed
* the percent char in first argument is special character
  * char after it specifies value type to be displayed

## All format specifiers

```c
#include <stdio.h>
#include <stdbool.h>

int main()
{
    int integer = 100;
    float floatpoint = 330.09;
    double doublenum = 8.44e+12;
    char character = 'U';
    bool Bool = true; // same as _Bool Bool = 1

    printf("integer = %i\n", integer);
    printf("floatpoint = %f\n", floatpoint);
    printf("doublenum = %e\n", doublenum);
    printf("character = %c\n", character);
    printf("Bool = %i\n", Bool);
    return 0;
}
```

|Format| Type |
|:---:|:-----:|
|`%i`| `int`|
|`%f`| `float`|
|`%e`| `double`|
|`%c`| `char`|
|`%i`| `bool, _Bool`|

## Precision in Floats

* there is a way to round off a float to a number of precision digits by using an operator
* instead of `%f`, use `%.nf` where `n` is the number of digits after the decimal point to round off to

```c
float floatpoint = 33.0909090909090909;

printf("2 digits is %.2f\n", floatpoint);
printf("5 digits is %.5f\n", floatpoint);
```

```cmd
2 digits is 33.09
5 digits is 33.09091
```

## More examples

![Taken from Programming in C, Kochan](https://lh3.googleusercontent.com/XZpDM4DCNOWG9V1wHCF3wbyQi_C4x1K92RQGPNua4Dm_6rMczS8OaghFQfmv3J60pgGYZ4SHlwVxkZvKjA4nziHf2eZZrJ8oHtnSTRVFtoQIkcjWREUSYJ0z50EnaA3BDkzvMxySeJ9FqXn-eWN_Y3LIPyha8YuHACMMc6vaeFINwU3l-B9ycwyXKXAHEEUlqXs8W4OsQRtGHEc6TCBWoze1IFyHIMgjrnYUltI11kmgUw1XJf-gFE4wg9Y52XqYkupjofLFX8yUGoqPdstb6-bEaM1Wybhfh3YZt_pG4w3lr-wrovtzTkfwAFNg83qk6niMTLP_7eMbo8fK79kjsPYFO9Al7wpeqirWCiSc3qsEWpAtLKovdY4VlJeoIrMspcUT0di6nLFuZfLgcdtJ18t2DroO9sOSSgfpEPU5glZJ5L764FwXVWt8EXNrhEngRbzq7dcHGMx4_30nU84d7LXnNz8yhRgSmubKe-PnszdVEOFrQ7QmSUIu_k_D87zd2IpFPOWOuYZdWj3sfd3DqUmeSikQ4pNTNDuoKoyqZzF7-0wvMxV4ngt3FZz3uEk2pmIKF-zULwFCIMpGKc3O3pIJeGqZJXAHGIMTaUnvCsvhYv8kz_cZnBS8_RpFwdv6etEWk3hfSGH-7Cgky2NHaj9pFGHBA6pHjB6dgBIBSmRNPJOwoc9ckgJqJsQJzw=w738-h451-no?authuser=0)
