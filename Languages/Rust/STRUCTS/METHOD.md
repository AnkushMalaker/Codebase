# Method stuff

Methods are similar to functions and are declared with the fn keyword. 
Difference being that they're defined within the context of a struct and their first param is always self.  

To define a fn within the scope of a strcut, we use `impl` block, and in the function, add the &self param. When we want to call this function we use the _method syntax_ with the . operator.  

Methods can take ownership of self, borrow self (immutably or mutably)


