# Using Structure Parameters to Functions

```c
typedef struct info {
    char gn[20];
    int age;
    char fatherGN[20];
    char motherGN[20];
} Info;

bool areSiblings(Info mem1, Info mem2) {
    if (strcmp(mem1.motherGN, mem2.motherGN) == 0) 
        return true; // if mother of mem1 and mem2 are the same
    else 
        return false;
}
```

# Pointers to Structure as Function Arguments

- you probably should use pointer to structures as arguments instead of structures themselves
    - since C passes by value, it takes quite a long time to copy the value of a large structure to a function
    - pointers avoids the memory consumption and saves time copying

```c
bool areSiblings(Info *mem1, Info *mem2) {
    if (strcmp(mem1->motherGN, mem2->motherGN) == 0) 
        return true; // if mother of mem1 and mem2 are the same
    else 
        return false;
} // saves time
```

- you can use `const` to not allow modification of struct member values

```c
bool areSiblings(const Info *mem1, const Info *mem2) {...}
```

- you can also use `const` to not allow modification of pointers' addresses

```c
bool areSiblings(Info *const mem1, Info *const mem2) {...} // not really useful
```

- here though, the `*const` is just redundant
    - since C only has the illusion of passing by reference (just copies address)
    - you can't change the address value of `mem1` and `mem2` outside the function

# Returning Structure from Functions

- function prototype should indicate the return value as a struct of a certain type

```c
struct StructName someFunc(void);
```

- this is a prototype for function taking no arguments and returns value of type `struct StructName`
- it's more convenient to just return a pointer to a structure
    - it's created on the heap and can take a tiny bit longer, but it uses less memory

## Example of Using Struct in Function

```c
#define ORG_LEN 101 // for 100 characters + null

typedef struct bankFunds {
    char bank[ORG_LEN];
    char save[ORG_LEN];
    double bankfund, savefund;
} bankFunds;

double fundSum (bankFunds *money) {
    return (money->bankfund + money->savefund);
}

int main(void) {
    bankFunds money;
    
    printf("Your bank is: ");
    scanf("%s", money.bank);
    printf("Your save is: ");
    scanf("%s", money.save);
    
    printf("Your money in %s is: ", money.bank);
    scanf("%lf", &money.bankfund);
    
    printf("Your money in %s is: ", money.save);
    scanf("%lf", &money.savefund);

    printf("From %s and %s, you have a total of ₱%.2f.\n", 
            money.bank, money.save, fundSum(&money));

    return 0;
}
```

```txt
Your bank is: Hello
Your save is: Hi
Your money in Hello is: 2000
Your money in Hi is: 5000
From Hello and Hi, you have a total of ₱7000.00.
```

# Some Reminders 🍟

- you should always use pointers when passing structures to a function
    - works on older as well as newer implementations of C
    - no need to worry about backwards compatibility
- you might have less protection for your data when using pointers
    - some operations could affect the data in the original structure
    - use `const` to solve the problem

    ```c
    double fundSum (const bankFunds *money) {...}
    ```

---

- advantages of passing structures to functions
    - function works with a copy of the structure, which is safer than tampering with the original data
    - programming style tends to be clearer
- disadvantages of passing structures to functions
    - older implementations may not work with the code
    - wastes time and memory
    - wasteful to pass large structures to a function that only uses one or two members

---

- many programmers use structure pointers as arguments for efficiency
    - use `const` when needed
- passing structures by value is done for small structures
