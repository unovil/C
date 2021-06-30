# Overview

- types of arrays we have talked about so far are linear arrays (one dimension)
- C allows arrays of any dimension to be defined (like nested lists)
- the most common are two dimensional arrays

Example:

```c
int matrix[4][5];
```

- this array `matrix` is a 2-dimensional array with 4 rows and 5 columns, for a total of 20 elements
- each dimension is its own pair of square brackets

# Initializing 2-dimensional Arrays

- same manner as linear arrays
- when listing, values are listed by row
- you put initial values for each row between braces, then enclose all between braces

```c
int matrix[4][5] = 
{
    { 10, 20, 30, 40, 50 },
    { 20, 30, 40, 50, 60 },
    { 30, 40, 50, 60, 70 },
    { 40, 50, 60, 70, 80 }
};
```

- inner pairs of braces are actually optional, but should be used for readability
  - **NOTE**: the braces are only optional as long as ALL columns are initialized

## Is it required to initialize everything? **Again, no.**

- as with linears, initialization for everything is not required

```c
int matrix [4][5] =
{
    { 10,  5, -3 },
    {  9,  0,  0 },
    { 32, 20,  1 },
    {  0,  0,  8 } 
};
```

- this only initializes first three elements of each row to indicated values
  - the 4th and 5th columns are set to 0
- in this case, the inner braces are REQUIRED to force correct initialization

# Designated Initializers

- subscripts can also be used like in 1D arrays

```c
int matrix[4][3] = 
{
    [0][0] = 1,
    [1][1] = 5,
    [2][2] = 9
};
// adjusting our minds for off-by-one error, we get the correct form:
int matrix[4][3] =
{
    {1, 0, 0}, // 0th row, 0th column
    {0, 5, 0}, // 1st row, 1st column
    {0, 0, 9}, // 2nd row, 2nd column
    {0, 0, 0}
};
```

# Other Dimensions?

- everything mentioned can also be adjusted and used for 3D arrays, etc.
- very rare tho

```c
int box[10][20][30];
// 6000 VALUES WHAT THE FU-
```

- typically, you'd use 2 nested loops for 2D arrays, 3 nested loops for 3D arrays, etc.  

## Visualization

- 1D arrays are a row of data
- 2D arrays are a spreadsheet or table of data
- 3D arrays are stacks of spreadsheets on top of each other
- 4D arrays are... well... hard to visualize

# Initializing more than 2D arrays

- process of initialization is extended
- a 3D array has 3 levels of nested braces

```c
int numbers[2][3][4] =
{
    {   // first block of [3]
        { 10, 20, 30, 40 }, 
        { 15, 25, 35, 45 },
        { 50, 51, 52, 53 }
    },
    {   // second block of [3]
        { 1, 2, 3, 4 },
        { 5, 6, 7, 8 },
        { 9, 10, 11, 12 }
    }
};
```

# Processing Elements with Loops

- you need nested loops to process all elements of the array
- level of nesting is number of dimensions
- each loop iterates over one dimension

```c
int sum = 0;

for (int a = 0; a < 2; ++a) // for every block in the array ( level 1 )
{
    for (int b = 0; b < 3; ++b) // for every array in that block ( level 2 )
    {
        for (int c = 0; c < 4; ++c) // for every element in that array ( level 3 )
        {
            sum += numbers[a][b][c]
        }
    }
}
