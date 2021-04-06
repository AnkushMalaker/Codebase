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

# I think I will come back to this topic later. Gonna cache it for now.
