# Generics 

We can use generics to create definitions for items like function signatures or structs, which we can then use with many different concrete data types.

## In function defintions
When defining a function that uses generics, we place the generics in the signature of the function where we would usually specify the data types of the parameters and return value.

`fn largest<T>(list: &[T]) -> &T {`  

This means: function `largest` is generic over some type T.  

## In struct definitions
Same as above, like `struct Point<T?>` and all data types in it have **the same** generic type T.  

To define struct where they can have diff types, we use `struct Point<T, U>`.  

## In enum definitions
Done before. Like `Option<T>` or `Result<T,E>`
## In method definitions
Use the `<T>` right after `impl`:  
```
struct Point<T> {
    x: T,
    y: T,
}

impl<T> Point<T> {
    fn x(&self) -> &T {
        &self.x
    }
}
```

