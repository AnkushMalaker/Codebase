# Defining and Instantiating Structs  

use keyword `struct` to define a struct and continue as any other language, giving the type along with it after a colon. Example:  
```
struct User {
    username: String,
    email: String,
    sign_in_count: u64,
    active: bool,
}
```
To use it, we have to define values for each variable in the struct as so:  
```
    let user1 = User {
        email: String::from("someone@example.com"),
        username: String::from("someusername123"),
        active: true,
        sign_in_count: 1,
    };
```

Accessing values can be done by dot: `user1.email` and if mutable, we can change the field using the same. (Entire instance must be mutable, not just a field)

If we use a constructor like function like `build_user()` we can use field init shorthand, ie, give the variable name the same as the name in struct to auto fill it. [As opposed to doing something like `email : email`]

We can create new instance with previous values and some changed using the _struct update syntax_  
This is normal way:  
```
    let user2 = User {
        email: String::from("another@example.com"),
        username: String::from("anotherusername567"),
        active: user1.active,
        sign_in_count: user1.sign_in_count,
    };
```

This is using struct update syntax:  
```
let user2 = User {
        email: String::from("another@example.com"),
        username: String::from("anotherusername567"),
        ..user1
    };
```

## Tuple structs  
No named fields. ex:  
`struct Color(i32, i32, i32)`  

## Unit-like structs w/o any fields  
This stuff will come later as its related to traits. 
If i remember, I'll come back and add it in. 

## Displaying a struct  
Calling `println!` macro with the `{}` tells println to use the Display method. Structs dont have inbuilt display methods but we can still use `{:?}` to display their information. This uses the `Debug` trait. 
We need to enable the debuggin for the struct explicitly using the `#[derive(Debug)]` before the struct for this to work.  


