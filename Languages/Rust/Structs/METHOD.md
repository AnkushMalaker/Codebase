# Method stuff

Methods are similar to functions and are declared with the fn keyword.
Difference being that they're defined within the context of a struct and their first param is always self.

To define a fn within the scope of a strcut, we use `impl` block, and in the function, add the &self param. When we want to call this function we use the _method syntax_ with the . operator.

Each struct can have multiple impl blocks.
Methods can take ownership of self, borrow self (immutably or mutably)

## Associated functions

These functions don't take the self param. Example is the String::from function.  
These are often used to return a new instance of the struct.
