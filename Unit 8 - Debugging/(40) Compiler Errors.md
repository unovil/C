# Overview

- very hard to understand what compiler error is happening
    - need to know compiler errors to fix them
    - difficult to identify reason behind compiler error

- compiler makes decisions on translating code that programmer hasn't written
    - convenient because progrms can be written more succinctly
    - (only expert programmers take advantage)
  
- when compiling, use option for compiler to notify all cases where there are implicit decisions
    - option is `-Wall`

# Types of Problems

## Errors

- prevents creation of final program
- no exe is made until all errors are corrected
- first errors are most reliable
    - there are some errors that may derive from previous ones

## Warnings

- messages compiler shows about situations where anomaly is detected
- non-fatal errors
- final exe may be obtained with any # of warnings
    - even if final compiles, it's possible that it won't work properly
- never consider program correct until all warnings are eliminated

# Common Compiler Messages

- 'variable' undeclared (first use in this function)
    - one of the easiest and most common messages
    - variable is used but hasn't been declared yet

  ```c
  printf("%d", var);
  // where is 'var' declared?
  ```

- warning: implicit declaration of function '...'
    - compiler finds function in code but no information about it
    - function is used before it's declared
    - to solve, use function prototypes

  ```c
  void main() {
    doThis();
  }

  void doThis() {}
  ```

- warning: control reaches end of non-void function
    - function is defined to return a result but no `return` is used
    - either function is not defined or statement is missing

  ```c
  int main() {
    printf("Hello");
    // where is return 0; ?
  }
  ```

- warning: unused variable '...'
    - variable is declared but not used

  ```c
  char args[5];
  // where is args used?
  ```

- undefined reference to '...'
    - function is invoked in code but not defined anywhere
    - reference to function with no definition
    - make sure definition is compiled

  ```c
  printf("Hello");
  // where is stdio.h?
  ```

- error: conflicting types for '...'
    - two definitions of function prototype is found
        - one is prototype (result type, name, params, semicolon)
        - other is definition with function body
    - information in both prototypes are not the same, conflict is detected
    - compiler shows which line conflict appears and previous def that caused error

  ```c
  void doThis(int someNum);
  int main() {
    ...
  }
  int doThis() {...} // NOT THE SAME PROTOTYPE!!
  ```

# Runtime Errors

- execution can crash when run-time error is detected
    - C programs only print succinct message "Segmentation fault"
    - results in core file, depends on signal thrown
    - analyze call stack and core file
