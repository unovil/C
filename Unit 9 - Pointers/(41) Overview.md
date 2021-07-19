# Indirection

- pointers are ver similar to concept of indirection

## Example

- say you need to buy a new ink cartridge for a printer
- all purchases are handled by purchasing department
    - you're calling Joe in purchasing and ask him to order that cartridge for you
    - Joe calls local supply store to order cartridge
- you are not ordering it directly from the supply store (indirection)
  
## Indirection

- the ability to reference something with name, reference, or container
    - instead of value itself
- most common form is to manipulate value through memory address

- pointer provides indirect means of accessing value of a data item
    - variable whose value is a memory address
    - value is address of another location in memory with a value

## Uses

- just as there are reasons to go through the purchasing department to order new cartridges
    - (you don't have to know which store the cartridges are bought from)
    - there are good reasons to use pointers

- compiler needs to know type of data stored in variable that pointer points to
    - also how much memory is occupied or how to handle the content to which it points
    - every pointer is associated with specific var type
    - can be used to only point to vars of that type
    - example: `int *var` can point only to vars of type `int`

# How a Pointer Works

<img
  src = "../pictures/pointer example.png"
  alt = "Pointer example"
  style = "display: block; margin-left: auto; margin-right: auto"/>

- the value of `&number` is the address (memory location) where `number` is located
    - this value is used to initialize `pNumber`
- `pNumber` points to the address of `number`

## Why use pointers?

- accessing data with variables is limiting
    - with pointers, you can access any location on memory
    - you can also do pointer arithmetic
- pointers make it easier to use arrays and strings
- pointers can refer to same space in memory from many locations
    - you can update memory in one location and change is seen from another in the prgram
    - can also save space by being able to share components in data structures
- pointers allow functions to modify data passed as variables
    - passing by reference: passing arguments in such a way that they can be changed by function
- pointers can be used to optimize program memory
- pointers allow us to return many values from a function
    - function can't return arrays, but passing args as pointers we can get more than one value from the pointer
- pointers can be used for dynamic memory which is created according to program use
    - we can save memory from compile-time (static) declarations
- pointers can design complex data structures like stacks, queues, and linked lists
- pointers provide direct memory access
