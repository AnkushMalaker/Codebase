# Variables and constants

- Variables are immutable by default, use mut to declare as mutable
- Constants are like **always** immutable variables and the type must always be annotated, declared using the const keyword.
- Only constants can be set to constants, not the result of a fucntion call or anything that can come only during runtime.

## Shadowing

Declaring a new variable with the same name allows us to shadow it, which is, second variables value appears whenever it is used.  
Use `let` keyword to shadow variable. Example:

```
let x = 5;

let x = x + 1;
```

Shadowing is different from marking a variable as `mut` as

1. We'd get a compile time error if we try to reassign an immutable variable without using the `let` keyword. Consider this `temporarily mutable` I guess?
2. Let essentially creates a new variable so we can change the type. We can't do this with `mut`.

# Data Types

- Scalar Types
  - Integer
  - Floating point
  - Boolean
  - Characters
- Compounded Types
  - Tuple (fixed length)
  - Array
