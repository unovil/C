# Debugging

- process of finding and fixing errors in program
    - usually logic, but can also be syntax err
- for syntax errors, understand what compiler is telling you
    - always focus on the first error
    - it's likely that other errors may be caused by first error
- can range from simple errors to collecting large data for analysis
- ability to debug is essential skill
    - can save amounts of time and money
- maintenance phase is most expensive phase of software life cycle
    - maintenance is fixing bugs after release
    - also includes adding features to the software
- bugs are unavoidable
    - nobody is perfect, and language rules may change over time

# Errors

## Logic Errors

- program compiles and there are no 'errors'
- it's not doing what it's intended to do
- 'this loop isn't iterating this number of times'

## Syntax Errors

- directly related to the compiler
- errors that don't follow the lanugage
- 'hey, you spelled `if` wrong'

## Memory Corruption

- major problem in C since lang doesn't have a disposal for memory
- if you leave used memory and not allocate them, bad things happen
    - like dangling references
    - like overflows
    - like memory leaks

## Performance and Scalability

- code works as intended, logic works as needed
- problem is that maybe it's too resource expensive
    - maybe hardware couldn't support the program
- the code isn't really efficient

## Lack of Cohesion

- happens in functions
    - functions should be given one purpose only
- giving one function too many features is bad
    - when function is too big, it's hard to parse and fix errors
- would require redesign of program

## Tight Coupling (too many dependencies)

- happens when you use too many dependencies
    - means that functions rely too much on each other
- function is a block of code that should work on its own
    - depending on another function makes it hard to fix errors

# Debugging Process

1. understand the problem and check where the error is from
2. reproduce the problem
    - sometimes difficult to do
    - some problems (like memory and threading) may occur on very specific circumstances
3. simplify the problem, divide and conquer, isolate source of problem
    - remove parts of the test case
    - comment out code and add other code to try tweaking it
    - unit testing
    : turn large program into many small programs
4. identify origin of probelm in the code
    - use debugging tools if needed
5. solve and fix the problem
    - needs experience and practice
    - sometimes, you need to redesign and refactor the entire program
6. test every possible case

# Techniques

## Tracing and using `printf`

- output values of variables at certain points in the program
    - show the flow of execution
- can help isolate error

## Debugging

- monitor execution of program
    - stop it
    - restart it
    - set breakpoints
    - watch vars in memory

## Log Files

- usually for analysis
    - add good log statements to the code

## Monitoring Software

- run-time analysis of
    - memory usage
    - network traffic
    - threads and objects

# Common Debugging

## Exception Handling

- can identify catastrophic errors
- many languages have exception handling
    - unfortunately, C does not

## Static Analyzers

- analyze source code for set of known problems
    - semantic checker (won't analyze syntax)
    - can detect uninitialized vars, memory leaks, unreachable code, deadlocks, race conditions

## Test Suites

- automated tasks to run set of comprehensive system end-to-end tests

## Debugging after Crashing

- analyze the call stack
- analyze the memory dump (core file)

# Preventing Errors

- write high quality code
    - follow good design principles
    - follow good programming practices and etiquette

- use unit tests (automatically executed when compiling)
    - helps avoid regression
        - regression: accidentally introducing errors in code that was previously fine
    - find errors in code before delivering
    - TDD (test driven development)

- provide good documentation and proper planning
    - don't jump into code immediately
    - write design on paper, utilize pseudocode

- work in steps, test after each step
    - avoid too many changes at once
    - apply changes incrementally
    - helps reduce sources of bugs
