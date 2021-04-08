# Closures

These are anonymous functions which we can **save in a variable** or pass as args to other funcs.  
Closures can capture values from the scope in which they're defined (unlike funs).

## Defining Closures

Follows an `=` symbol and is defined using two pipes that enclose any parameters, followed by the function definition. The last line that doesn't end in a semi colon will be the one returned.

With `let myfunction = |num| {somedefinition}`, we only store the function definition (code) in the variable myfunction. We don't store the returned value. We can call it like any other function.

## Closure Type Inference and Annotation

Closures aren’t used in an exposed interface like functions: they’re stored in variables and used without naming them and exposing them to users of our library. They don't need annotation of types and params.

The compiler infers the types because closures are used in small contexts. If there are ambigus usages then it won't work.

## Memoization/Lazy Evaluatoin w/ Closures

We can make a struct that holds a closure and the output.
The `Fn` traits are provided by the standard library. All closures implement at least one of the traits: `Fn,` `FnMut,` or `FnOnce`

Best understand from example: 
```
struct Cacher<T>
where
    T: Fn(u32) -> u32,
{
    calculation: T,
    value: Option<u32>,
}
```
> The Cacher struct has a calculation field of the generic type T. The trait bounds on T specify that it’s a closure by using the Fn trait. Any closure we want to store in the calculation field must have one u32 parameter (specified within the parentheses after Fn) and must return a u32 (specified after the ->).


## FnOnce, FnMut, Fn  
- `FnOnce` consumes the variables it captures from its enclosing scope, known as the closure’s environment. To consume the captured variables, the closure must take ownership of these variables and move them into the closure when it is defined. The Once part of the name represents the fact that the closure can’t take ownership of the same variables more than once, so it can be called only once.
- `FnMut` can change the environment because it mutably borrows values.
- `Fn` borrows values from the environment immutably.

