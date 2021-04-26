# Nested Loop
- sometimes you might want to place a loop inside another
## Example 1
- say you want to count number of occupants in each house on a street
- you could go from house to house, and within each house count the number of occupants
- the house counting is the outer loop, and the occupant number is the inner loop

# `continue`
- sometimes you want to skip to the next iteration but not skip the loop entirely
- in these situations, add `continue`

- using this can sometimes eliminate nesting, which improves readability
## Example
```c
enum Day {M, T, W, TH, F, ST, SN};

for (enum Day day = M; day <= SN; ++day)
{
    if (day == W)
    {
        printf("It's Wednesday :(\n");
        continue;
    }


    printf("It's not Wednesday!!!\n");
    // do something with it
}
```
```
It's not Wednesday!!!
It's not Wednesday!!!
It's Wednesday :(
It's not Wednesday!!!
It's not Wednesday!!!
It's not Wednesday!!!
It's not Wednesday!!!
```
# `break`
- maybe you want to stop a loop entirely, not skip to next iteration
- if `break` is inside nested loops, it affects only the actual loop that has it
## Example
```c
char Number;
while (1 == 1) // infinite loop!! unless...
{
    printf("Put any digit: \n");
    scanf("%c", Number);

    // perhaps for debugging purposes...
    if (Number == 'C')
        break;
}