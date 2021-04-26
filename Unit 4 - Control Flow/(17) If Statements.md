# IF
- C provides decision-making capability in form of if statement
```
if ( expression )
    program statement
```

- For example, translating "If it is hot, I'll go swimming" is easy
```
if ( it is sunny )
    i'll go swimming
```
- curly brackets are needed for compound statements inside the if block

## Example
```c
int score = 95;
int big = 90;

if (score > big)
    printf("Jackpot!!!\n");

// since many, need braces
if (score > big)
{
    score++;
    printf("You win\n");
}
```
![](https://www.alphacodingskills.com/java/img/java-if.png)
# IF ELSE
- C can also execute a code block when the condition is false
- the `else` block is optional; it can be not used
```c
if (expression)
    Statement;
else
    Other statement
```
![](https://www.guru99.com/images/r_programming/032818_1241_IFELSEELIF1.png)
## Example
```c
#include <stdio.h>

int main()
{
    int number, remainder;
    
    printf ("Enter number to be tested: ");
    scanf ("%i", &number);

    // if number is odd, dividing it by 2 will give a remainder of 1
    // if number is even, dividing it by 2 will give a remainder of 0
    remainder = number % 2;

    if (remainder == 0)
        printf ("The number is even.\n");
    else
        printf ("The number is odd.\n");

    return 0;
}
```
# ELSE IF
- adds another layer of questioning
- like `elif` of Python
```c
if (expression1)
    statement1
else if (expression2)
    statement2
else
    statement3
```
![](https://i0.wp.com/code4coding.com/wp-content/uploads/2018/04/ifinpython.jpg?resize=467%2C413&ssl=1)
## Example
```c
// What's the sign of a number?
#include <stdio.h>

int main() {
    int number, sign;

    printf("Please type a number: ");
    scanf("%i", &number);

    if (number < 0)
        sign = -1
    else if (number == 0)
        sign = 0
    else
        sign = 1
    
    printf("The sign of %i is %i.\n", number, sign)
}
```
- As shown in the diagram, if the `if` statement is true already, it executes the codeblock in that `if` and continues, even if the `elif` statement is true
## Example
```c
int main() {
    // suppose number is 9
    int number = 9;

    if (number == 9)
        printf("Always true");
    else if (number > 5)
        printf("Will never be true");
    else
        printf("If the number is less than 5 only");
    return 0;
}
```
# NESTED IF-ELSE
- any `if` statements inside another `if` will be conditioned only when first `if` is true
```c
if (bool)
{
    // some expressions

    if (bool2)
    {
        // some other expressions
    }
}
```
```c
enum player {YOU, ME};
enum player playerToMove;
if (gameIsOver == 0) // false
    if (playerToMove == YOU)
        printf("Your turn!\n");
    else // playerToMove == ME
        printf("My turn!\n");
else // true
    printf("The game is over!");
```
# Conditional Operator (ternary operator)
- unique as it is the only operator to take 3 operands
- logical condition is before `?`
- statement when value is true is the second statement
- statement when value is false is the third statement
- can only take one expression
```c
x = y > 7 ? 25 : 50;

// same as
if (y > 7)
    x = 25;
else
    x = 50;
```
- a bit confusing to read, but basically it's an assignment
    - if `y` is greater than 7, then `x` is assigned a value of 25, otherwise it's assigned 50