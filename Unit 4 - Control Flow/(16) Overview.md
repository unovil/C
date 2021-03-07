# Control Flow
- statements inside source files are usually executed from top to bottom, line per line
    - known as sequential flow
- control flow statements beak up flow by asking for decisions, looping, and branching
    - enables program to conditionally execute certain blocks


| Type | Examples|
| :----: | :------ |
| Decision-making | if-then <br> if-then-else <br> switch <br>goto
| Looping | for <br> while <br> do-while
| Branching | break <br> continue <br> return

# Decision Making
- sturctures that specify one or more conditions to be tested
    - if condition is true, statement/s are executed
    - if not, other statements are executed or nothing executes

![](https://www.educative.io/api/edpresso/shot/5593231642329088/image/6209099250270208)

| Statement | Description
| :--: | :----
| `if` | boolean followed by one or more statements
| `if-else` | can be followed by optional `else`, executes when boolean is false
| nested `if` | you can use `if` and `else if` statements inside other conditionals

# Repeating Code
- there are situations where a block of code needs to be executed a number of times
    - statements are executed sequentially; first statement in function is executed first, then second, and so on

- loop statement can execute a number of times according to boolean
- when execution leaves scope, all automatic objects are destroyed
- loop is infinite if condition never is false
    - `for` is usually used for that

![](https://study.com/cimages/multimages/16/cb730cff-275e-4ff8-92c1-a309f5d1ff41_c_loop_flow.png)

| Statement | Description
| :--: | :----
| `while` | repeats statement while condition is true, tests condition before executing loop body
| `for` | executes sequence of statements many times and abbreviates code that manages loop var
| `do...while` | similar to `while`, but tests condition at the end of the loop body
| nested loops | can use one or more loops inside any other loop