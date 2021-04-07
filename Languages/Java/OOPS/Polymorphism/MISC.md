# Instance Initializer

Instance intializer block is invoked at the time of object creation. The java compiler copies the instance initializer block in the constructor after the first statement super(). So firstly, constructor is invoked. Java compiler copies code of instance initializer block in every constructor.

# Final Keyword

- Value of `variable` declared as final cannot change.
- Final `methods` can't be overridden.
- Final `Class` can't be extended.
- Blank final variable is final var that is not initialized at time of declaration. Static blank final variables. This can only be changed through static block.

# Super

Can be used to invoke parent class instance variable, method or constructor.

Its added in each class constructor automatically, like the default constructor.
