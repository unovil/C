# Call Stack

- generated when app crashes because of a fatal error
- known as 'stack' because a stack is a common data structure
    - part of a LIFO ("Last in, First out")
    - like the tower of Hanoi, when you place a disk on top, you retrieve that disk first
- very useful for analyzing in debug
- shows list of function calls leading to the error
    - includes filenames and line #'s of code that cause error to occur
    - **top of the stack** is last call that cause the error
    - **bottom of the stack** is call that started chain of calls to cause error
    - need to find call in the app that caused the crash
- you can also dump the call stack
