# Box<T>

The most straightforward smart pointer is a box, whose type is written `Box<T>.` Boxes allow you to store data on the heap rather than the stack. What remains on the stack is the pointer to the heap data

## Syntax

`let b = Box::new(5);`

## Cons

"To cons x onto y" -> construct new container instance by putting x at the start of new container followed by container y.

This kind of a thing will not be implemented normally in rust becasue it will be of infinite size. To break the chain we can define the Box type over the second element. Now the second element is a pointer and for each item we have defined size of (size of x, size of box).

**We can use this to create recursive type**
