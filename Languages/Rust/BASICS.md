# Basics of the rust language.  

I will be ommitting everything that's mostly common to every other programming language such as how control structures and looping constructs work.  

First off, rust uses 4 spacse for indentation instead of a tab. I'm not sure how I could possibly use this language now that I know this. (/s)  

-  Rust is compiled  
-  Main is the first thing that runs in the program  
-  The libraries are statically linked (All libraries requird are put in the exe during compulation including the rust runtime)  
-  Cargo is the most used "manager" for rust. It handles adding dependencies and compilation.  
  
## Cargo  
Create new project with cargo:  
`cargo new hello_cargo`  

The dependencies are put in the `cargo.toml` file

### Building a project with Cargo:  
`cargo build` 
This puts a build in the target/debug directory. Running this for the first time also creats cargo.lock which manages, automatically all the dependencies that the program would need.  

// We can also just do `cargo run` to compile and run.  

`cargo check` checks if the code compiles but doesnt produce an executable.  

To build for release, just do  
`cargo build --release` 
This adds in the optimizations but takes longer to compile. 


## Inputs and outputs  
When calling a function, its done simply via function\_name(), but when calling a macro, its done via macro\_name!(). println! is a macro used to print on screen. 
For taking inputs, we use the io library by calling `use std:io;` 

So to take input from user and store it in a variable called guess, we'd have to call the stdin() from io. Then, use the read\_line(&mut guess) method to store it in the variable guess.  
The & represents that the argument is a reference, which are also **immutable** by default. This is why we must put &mut guess instead of &guess, so that we can make it mutable. 

To output the value, we can use a placeholder in the println statement, like using %d in C. Here, we use { } to denote a placeholder.  

## Variables  
To create a variable we use the `let` keyword. 
`let foo = bar;`  
Variables are **immutable** by default so we must give the mut keyword before variable name to make it mutable.  

To declare the data type of the varible, we can provide the datatype using = symbol.
`let mut guess = String::new();`

The `::` in the above code explains that `new` is an **associated function** or the String type. 
## Crates
Creates are a colection of rust source code files. 
To add extenal crates (Libraries), put it under dependencies like so: 
```
[dependencies]
rand = "0.5.5"
```

To get a documentation of all the creates in your program, run:  
`cargo doc --open`  


