# Variable-Length Arrays

- so far, all sizes of an array have been specified using a number
- 'variable' in variable-length array does not mean you can modify length of array after creating it
  - VLA keeps same size after creation
- introduced in C99

# Valid and Invalid Declarations

```c
int n = 5;

float a1[5];                    // yes for positive integers
float a2[5*2 + 1];              // yes for expressions
float a3[sizeof(int) + 1];      // yes for other complex operators
float a4[-4];                   // no, size > 0 only
float a5[0];                    // no, size > 0 only
float a6[2.5];                  // no, size must be int
float a7[(int)2.5];             // yes, casting is allowed
float a8[n];                    // n is a VLA, this wasn't allowed before C99
```
