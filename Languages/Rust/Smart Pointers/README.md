# Smart pointers

Pointer is general. Simplest pointer in rust is the reference and nothing much else.

Smart pointers on the other hand are data structures that act like pointers but also have meta data and capabilities.

References only borrow data, smart pointers own the data. `String` and `Vec<T>` are smart pointers.

Smart pointer are implemented using Structs but diff is that they also implement

- `Deref` _trait_: Allows instance of smart pointer to behave like a ref.
- `Drop` _trait_: Customize code that runs when instance of smart pointer goes out of scope.

The drop trait gets audo run whenever an object goes out of scope. To do it manually, we have tou se the `std::mem:drop` function. When we do this, whatever drop method we have defined in the function will also get called.

## Rc<T> Reference counted smart pointer

Used to enable multiple ownership. Value is cleaned up if reference count is 0.  
Defined in the same way as Box, like Rc<T>. (`Rc<List>`)
To add ownership of some `a` from `b` and `c`, we'd do `Rc::clone(&a)` from both `b` and `c.`
We can see the reference count of `a` by doing `Rc::strong_count(&a)`.

## RefCell<T> and interior Mutability Pattern

With RefCell<T> the borrowing rules are enforced at _runtime_ rather than at compile time. The RefCell<T> type is useful when you’re sure your code follows the borrowing rules but the compiler is unable to understand and guarantee that.

### Interior Mutability: mutable borrow to immutable val

Interior Mutability means that varaible can be changed by its methods but be immutable to everything outside.

// I don't really see the use caes for this right now, I will come back to this whenever I find that it will be useful.
