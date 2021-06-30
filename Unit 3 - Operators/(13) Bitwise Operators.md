# Bitwise Operators

## Bitwise

C offers bitwise logical and shift operators

* look like logical operators, but different
* operate on bits in integer values
* not used commonly

One major use of bitwise AND `&` and bitwise OR `|` is to test and set individual bits in integer variable

* can use bits to store data

You could use single integer var to store many characteristics of person, like

* whether male or female
* to specify what the person speaks
* another to record the salary
* in four bits you can have a set of data recorded

## Binary Numbers

* a number that includes only one and zero
* could be of any length

| example | base-10 |
| :-----: | :------: |
| 0| 0
| 1| 1
| 10| 2|
| 11 1111| 63 |
| 111 1111 1111 1000 | 32 760 |

## Operators

| Symbol | Meaning |
| :----: | :------ |
| `&` | bitwise AND, takes two operands and does AND on every bit pair, returns 1 in the final result if both are 1
| `\|` | bitwise OR, takes two operands and does OR on every bit pair, returns 1 on final if at least one is 1
| `^` | bitwise XOR (exclusive or), takes two operands and performs XOR on every pair, returns 1 if only one of them is 1
| `<<` | left shift, takes two numbers, moves bits of first to the left by number of places decided by second (effectively multiplying by powers of 2 on binary)
| `>>` | right shift, takes two numbers, moves bits of first to the right, by number of places decided by second (dividing by powers of 2 on binary)
| `~` | Flips the binary number (makes all 1s to 0s, all 0s to 1s)

* Be careful in using the left and right shift, and the tilde on unisgned integers, since they hold 32 bits (on most computers. to check if yours is, use `sizeof()`)

For more info and examples, go to [GeeksForGeeks](https://www.geeksforgeeks.org/bitwise-operators-in-c-cpp/#:~:text=The%20%26%20(bitwise%20AND)%20in,every%20bit%20of%20two%20numbers.).
