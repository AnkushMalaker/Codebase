# Basics of crates/packages etc

Cargo passes the crate root files to rustc to build the binary or library.  
If a packages has `src/main.rs` and `src/lib.rs` then it has two crates, a binary and a library.

## Creaating library

Create a new library named restaurant by running `cargo new --lib restaurant`

## Modules

Modules

- Organize code within a crate into groups for readability and easy reuse
- Control the privacy of items

Contents of either main.rs or lib.rs form a module called crate at the root of the crates module structure known as _module tree_.

### Defining modules

Define a module by starting with the mod keyword and then specify the name of the module

### Paths

Path to a fn or somehting in module tree can be two ways:

- Absoute path
- Relative with `self,` `super` or some identifier.

**The way privacy works in Rust is that all items functions, methods, structs, enums, modules, and constants)( are private by default.)**

#### Exposing paths with `pub` Keyword

The `pub` keyword lets code in its ancestor modules refer to it.
(If we simply make a module public, its contents will still be private. We need to make public the contents indivisually. )

If we we a struct public with `pub,` its fields will still be private so make them public with a `pub.`
The `super` keyword is like the `..` in the filesystem analogy where we can start relative path with the parent.

#### Paths with use keyword

Brings keywords into scope once and can be used again like local items.
This is like creating a symbolic link in the file system.

Bringing the parent module in using `use` allows us to know where a function comes from when calling in.

This doesn't apply to structs, enums and other items that use `use`, bring in the full path there.

We can rename paths using `as` keyword:  
`use std::io::Result as IoResult`

The brought in name is going to be **private**. So we can combile `use` and `public` to make it public and allow others to call it as if it belongs to our code.

#### Nested use lists

This code:

```
use std::cmp::Ordering;
use std::io;
```

can be  
`use std::{cmp::Ordering, io}`

We can bring everything in a path to scope using `*`.  
`use std::collections::*`

### Separating modules into diff files

In `lib.rs` if we do `mod some_module;`, it tells rust to load module with that name from different file. (As opposed to creating a block after the module name.)
