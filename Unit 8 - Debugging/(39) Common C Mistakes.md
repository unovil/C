# Very Common Mistakes

- misplacing semicolon

  ```c
  if (j == 100);
    j = 0;
  ```

    - `j` will always be 0
    - semicolon is syntactically valid and no compiler errors are produced
    - also made in while and for loops

- confusing `=` with `==`

  ```c
  while (j = 100) { printf("%d\n", j); --j}
  ```

    - also not compiler error
    - usually inside `if`, `while`, and `for`
    - assigns `100` to j, then executes printf call
    - `printf()` always called because value of expression is nonzero

- omitting prototype declarations

  ```c
  // squareRoot (int num);

  void main() {
    result = squareRoot(2);
  }

  squareRoot(int num) {...}
  ```
  
    - a bad idea, you should always add prototype declarations
    - if not, there may be errors from implicit declarations
        - functions are being used before they're being defined

- not using header file for definition for C lib function in program

  ```c
  // #include <math.h>

  void main() {
    double answer = sqrt(v);
  }
  ```

    - if you don't include `math.h`, compiler produces implicit declaration error

- confusing character and string

    - `'a'` is different from `"a"`
        - `'a'` is a single char
        - `"a"` is a pointer to char array `{'a', '\0'}`

- using wrong bounds

  ```c
  int a[100], i, sum = 0;

  for (i = 1, i <= 100; ++i) sum += a[i];
  ```

    - arrays in C are 0-indexed
        - `a[i]` points to second pos in `a`
        - `a[100]` points to 101st pos in `a`
    - `a[100]` isn't good since you're pointing to something that doesn't exist in array
        - only from `0, 1, 2... 98, 99` for a total of 100 places

- forgetting an extra loc in array for null char

  ```c
  char text[5] = {'h', 'e', 'l', 'l', 'o'};
  ```

    - when declaring char arrays, needs to be large enough to have null
        - string `"hello"` needs six places in char array to reserve for null

- confusing operator `->` with operator `.` when referencing struct members
    - `.` is used for structure variables
    - `->` is used for structure pointer variables

- omitting ampersand before non-pointer variables in `scanf()`

  ```c
  int number;
  scanf("%d", number);
  ```

    - all args after `scanf()` must be pointers (like strings)
    - you can make a variable a pointer by adding `&`
        - this will point to the **address of `number`**

- using pointer var before initialization

  ```c
  char *charpt;
  *charpt = 'X';
  ```

    - you can only apply dereference operator `*` to pointer var if set it to point somewhere
        - since `charpt` never pointed anywhere, where would `'X'` go?
    - causes segmentation fault

- ommiting `break` at end of each case in `switch` block

  ```c
  switch (number)
  {
    case somenumber:
      // statements
    default:
      // def statements
  }
  ```

    - if break not included, execution of statements continues to next case (in this case it's `default`)

- inserting semicolon at end of preprocessor

  ```c
  #define NUMBER 99;
  ```

    - usually happens because of habit
    - leads to syntax error
        - preprocessors are used for enhanced performance
    - for example, `if (value == NUMBER)` will be interpreted as `if (value == 99;)`

- omitting closing parenthesis or closing quotations on a statement

  ```c
  float total = (pow(a, 2) + 5 * 3;
  printf("Your total is %.2f, total);
  ```

    - use of parentheses makes code more readable
        - always a possibility of missing closing parenthesis
    - a compiler error
        - sometimes, error is misleading
        - compiler catches error on the next line
