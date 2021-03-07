# Arithmetic Operators
* math func that takes two operands and performs calculation between them <br>

If for example `a = 10` and `b=20`:
| Operator | Description | Exmaple |
| :-------: | :---------- | :----- |
| `+` | Adds two operands| `a+b` =30
| `-` | Subtracts second operand from first | `a-b` =-10
| `*` | multiplies operands | `a*b` =200
| `/` | divides numerator by denominator | `b/a` =2
| `%` | modulus operator, remainder after division | `b%a` =0
| `++` | increment, increases integer by 1 | `a++` or `++a` =11
| `--` | decrement, decreases integer by 1 | `a--` or `--a` =9
## `++a` or `a++`?
* say for example we have this bit of code:
```c
#include <stdio.h>

int main() {
    int a = 5;
    printf("The incremented value of a is %d\n", a++);
    
    return 0;
}
```
```cmd
The incremented value of a is 5
```
* the reason is that `a++` means that this operation executes **after** the printf
* to change this, use `++a`, which executes **before** the function
```c
#include <stdio.h>

int main() {
    int a = 5;
    printf("The incremented value of a is %d\n", ++a);
    
    return 0;
}
```
```cmd
The incremented value of a is 6
```
# Logical Operators
* also known as a Boolean Operator
* returns Bool based on result of one or two other expressions

if for example `a = true`, `b = true`, `c = false`, and `d = false` (when including preprocessor `stdbool.h`)
| Operator | Description | Exmaple |
| :-------: | :---------- | :----- |
| `&&` | AND operator, returns `true` (1) if both operands are true, `false` (0) if at least 1 of them are false| `a&&b` = 1
| `\|\|` | OR operator, returns `true` (1) if at least one operand is true |  `a\|\|d` = 1
| `!` | NOT operator, retunrs the opposite bool of the expression | `!(a&&d)` = 1 
# Assignment Operators
* assigns value of expression (right side) to variable (left side)

if `a = 1` and `b = 2`
| Operator | Description | Exmaple |
| :-------: | :---------- | :----- |
| `=` | simple assignment | `a = 1`
| `+=` <br> `-=`<br> `*=`<br> `/=`<br> `%=` | operate and assignment operator. performs operation of two operands, plugs result back into the left variable | `a+=b`, so `a = 3` <br> `a-=b`, so `a = -1` <br> `a*=b`, so `a = 2` <br> `b/=a`, so `b = 2` <br> `b%=a`, so `b = 0`
# Relational Operators
* compares variables against each other

for example `a = 2`, `b = 2`
| Operator | Description | Exmaple |
| :-------: | :---------- | :----- |
| `==` | if two operands are equal, return true | `a == b` = 1 (true)
| `!=` | if two operands are not equal, return true | `a != b` = 0 (false)
| `>` | if left operand is greater than right, return true | `a > b` = 0 (false)
| `<` | if left operand is less than right, return true | `a < b` = 0 (false)
| `>=` | if left operand is greater than or equal to right, return true | `a >= b` = 1 (true)
| `<=` | if left operand is less than or equal to right, return true | `a <= b` = 1 (true)