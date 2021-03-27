# Ownership  
This is what allows rust to perform without garbage collector.  

## Stack vs Heap:  

- Stack is a LIFO datastructure. All data stored on the stack must have a known, fixed size.
- Data with an unknown size at compile time or a size that might change must be stored on the heap instead.
- The heap is less organized: when you put data on the heap, you request a certain amount of space. The memory allocator finds an empty spot in the heap that is big enough, marks it as being in use, and **returns a pointer**, which is the address of that location. This process is called allocating on the heap and is sometimes abbreviated as just allocating. Pushing values onto the stack is **not** considered allocating. Because the pointer is a known, fixed size, you can store the pointer on the stack, but when you want the actual data, you must follow the pointer.
- Stack is faster than heap since only pointer has to be noted for. Pushing to stack also faster since it doesnt have to do memory allocation or bookkeeping.  

## Ownership Rules:
- Each value in Rust has a variable that’s called its owner.
- There can only be one owner at a time.
- When the owner goes out of scope, the value will be dropped.

To demonstrate the stack vs heap thing, 
// String literals are stored on stack, String is stored in a heap structure. 
We can create a string from a literal using  
`let mut s = String::from("somestring")`  
And we can push onto this string now, using `s.push_str(", somethingelse")`  

## Memory and Allocation  
The allocatoin of the memory for the string happens when we call the `String::from` method.  The dispoing of the memory happens in rust when the variable that owns it goes out of scope. 

When variable that owns s runs out of scope, Rust calls a spl func called `drop` at the closing curly bracket of the owner.

### Double free error
If we have `x = 3; y = x`, we have two variables x and y. If we have `x = String::from("hello"); y = x`, we will have two strings pointing to the same place in the heap. Now if both x and y go out of scope, they will try to free it together.  This can lead to memory corruption, thus, when we so y = x incase of strings, Rust declares s1 as invalid so no need to free memory in that case.  

It _moves_ the data from the first variable to the second (Not actually moving anything in memory). The consequence of this is that:  
**Rust will never automatically deepcopy any data**. 
To deepcopy we may use the `clone` method.  


This isn't the case in terms of stuff stored on stack, like integers. This can be be deepcopied directly with `y = x` since stack operations are inexpensive.  

## Ownership and Functions 
