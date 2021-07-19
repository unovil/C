# Nested Structures

- structures within structures
- say you have two structures, Date and Time, and your program is required to use these together for recording the date and time of an event.

```c
struct date { int month, day, year; };
struct time { int hours, minutes; float seconds; };

struct DateTime {
    struct date Date;
    struct time Time;
};
```

- variables can now be defined as of type `struct DateTime`

```c
struct DateTime dt;
```

## Accessing Members of Nested Structure

- syntax is same as referencing any member (but this time it's nested)

```c
dt.Date.month = 5; // sets Date month to 5
++dt.Time.seconds; // sets Time seconds to 1.00
```

## Initializing Nested Structure

- event variables are initialized like normal

```c
struct DateTime dt = { {3, 2, 2015}, {3, 30, 0} };
// March 2, 2015 at 3:30:00
```

- you can use member names in initialization

```c
struct DateTime dt = {
    { .month = 2,     .day =  1, .year    = 2015 },
    { .hour  = 3, .minutes = 30, .seconds =    0 }
};
```

# Arrays of Nested Structures ＼（〇_ｏ）／

- it's fine to set an array of DateTime structures

```c
struct DateTime events[10];
```

- array contains 100 elements of type `struct DateTime`
    - fourth `DateTime` in array is referenced as usual

```c
// increment the month of the 4th element of events[]
++events[3].Date.month;
```

# Declaring a Structure within a Structure

```c
struct Time {
    struct Date {
        int day;
        int month;
        int year;
    } date;

    int hour;
    int minutes;
    int seconds;
};
```

- very limiting though
    - this declaration is enclosed within scope of `struct Time`
    - it's impossible to declare a `Date` variable by itself, you always have to use `Time`
