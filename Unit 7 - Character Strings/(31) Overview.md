# Strings
- to assign a single character to a `char`, enclose with single quotes
```c
char plusSign = '+';
```
- there is a difference between single and double quotes
```c
char plusSign = "+" // wrong if plusSign is char
```
- a string constant or literal is a sequence of characters/symbols in double quotes
    - anything in double quotes is a string
    - includes any special characters and embedded spaces
## Note about `printf()`
```c
printf("For \" write \\\". ");
// For " write \". 
```
- for this example, adding double quotes normally would be interpreted as a delimiter
    - add an escape sequence instead `\"`
- also adding `\` confuses compiler since anything after it is part of escape seq.
    - add `\\` instead
# Null Character
- special char with code value `0`
- added to the end of each string to mark where it ends
- this is known as `\0`
- a string is always terminated by this,
    - so string length is always one more than number of chars in string
```c
char hello[6] = "hello"; // this is "full", same as
char hello[6] = {'h', 'e', 'l', 'l', 'o', '\0'}; // see the null? it's there
```
## null character vs. NULL
- don't confuse the two, very different
- null character is a string terminator
- NULL is a symbol that means the memory address does not reference anything
## Example
```c
int main(void)
{
    printf("The char \0 ends the string.");
}
```
- the output is `The character `
    - only first part is displayed
    function stops when it reached the null char
    - anything after it will not be reached
    - `\0` always marks end of string
