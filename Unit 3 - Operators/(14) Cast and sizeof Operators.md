# Type Conversions
- conversion of data between different types can happen implicitly by C, or explicitly by program
- normally you shouldn't mix types, but there are times when they're useful
## Float and Int
- when float is assigned to int in C, decimal portion is truncated
```c
int x;
float y = 2.54;
x = y;
// x is just 2
```
- when int is assigned to float, nothing happens, other than putting a `.0`
```c
int x = 3;
float y;
y = x;
// y is 3.0000...
```
## Arithmetic
- if two operands are integers, then any decimal part in division is truncated, even when assigned to float
- if only one operand is an int, operation is performed as float operation
# Cast Operator
- you can demand the precise type conversion you want
- consists of preceding the quantity with desired type in parentheses
    - the parentheses and type name constitute the cast operator (like `(int)`)
- has higher precedence than all arithmetic operations except unary plus and minus
```c
x = (int) 21.51 + (int) 26.99
// now, x = 21 + 26
```
# sizeof Operator
- tells how many bytes are occupied in memory by a given type
- it's a special keyword for operations, not a function
- evaluated at compile time, not at runtime, unless variable-length array is used
- argument can be variable, array name, basic data type, derived data type, or expression
- use it wherever possible to avoid calculating and hardcoding sizes
# Other Operators
- asterisk to variable `*var` represents a pointer to a variable
- `?:` is used for comparisons
    * if condition is true `?` then value `x:` otherwise value `y`
    * called as ternary operator
    * check out [freeCodeCamp](https://www.freecodecamp.org/news/c-ternary-operator/#:~:text=The%20ternary%20operator%20take%20three,result%20upon%20a%20false%20comparison) for more info