# Overview
- operator precedence determines grouping of terms in expression
- decides how expression is eval
- certain operators have higher precedence than others
```c
int x = 7 + 3 * 8;
// multiplying comes first, so 24
// add 7 to 24, you get 31
```
- to group expressions, use parentheses, since anything in parentheses is executed first
# Associativity
- if two operators have same precedence, associativity rules apply
- if sharing operand, executed usually from left to right
```c
1 == 2 != 3 // this is (1 == 2) != 3
// this evaluates to
0 != 3
// which is
1
```
# Operator Precedence
![](https://discuss.codechef.com/upfiles/C.PNG)
* `->` is for pointers, so it's not yet discudded
