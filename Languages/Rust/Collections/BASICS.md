# Vectors

Store values of a single data structure next to each other.

## Creating a vector

`let v: Vec<i32> = Vec::new();`
The `Vec<T>` is required because right now the compiler doesn't know what kind of value is going to be stored. Rust can instead _infer_ the type of value during declaration using the `vec!` macro.  
`let v = vec![1, 2, 3]`

## Usage of vector

### Pushing values

This can be done using `v.push(5)`
Note that this requires v be declared with `mut` keyword.

```
let mut v = Vec::new)();
v.push(5);
```

Here, rust checks the values and infers the i32 type.

### Dropping vector

When the vector goes out of scope, all elements are dropped including the vector.

### Reading elements of vectors

This can be done using:

- `get`
- `&v[3]`

Both are illustrated here:

```
    let v = vec![1, 2, 3, 4, 5];

    let third: &i32 = &v[2];
    println!("The third element is {}", third);

    match v.get(2) {
        Some(third) => println!("The third element is {}", third),
        None => println!("There is no third element."),
    }
```

1. get
   The .get() method gives us an _Option<&T>_  
   If the index passed within the get is outofbounds, rust returns None without panicking.

2. & and []
   The & and [] method gives us a _reference_  
   If the value passed within [] is outofbounds, rust exits the program. This is best used if we want the app to crash in case of a reference outofbounds is asked.

We can't borrow mutable and immutable reference to a vector in the same scope, so this won't compile:

```
let mut v = vec![1, 2, 3, 4, 5];

    let first = &v[0];

    v.push(6);

    println!("The first element is: {}", first);
```

> This error is due to the way vectors work: adding a new element onto the end of the vector might require allocating new memory and copying the old elements to the new space, if there isn’t enough room to put all the elements next to each other where the vector currently is. In that case, the reference to the first element would be pointing to deallocated memory. The borrowing rules prevent programs from ending up in that situation.

## Iterating over vector

We can simply use a for loop with a reference to the vector and convenient syntax for this.

```
let mut v = vec![100, 23, 11];
for i in &mut v {
	*i += 50;
}
```

Obviously, don't use a mutable reference if you don't want this value to be changed and only accessing it.

## Storing multiple values

We can use enums (when we know the exact types that we will get, at compile time) and traits(if we don't). Traits will be discussed later and I'll add it here if I remember to for the sake of completeness of this. If I haven't, create an issue please :)

```
    enum SpreadsheetCell {
        Int(i32),
        Float(f64),
        Text(String),
    }

    let row = vec![
        SpreadsheetCell::Int(3),
        SpreadsheetCell::Text(String::from("blue")),
        SpreadsheetCell::Float(10.12),
    ];
```

# Strings

Rust core-language only has str string slices (String literals are also string slices). The other String we know is actually an implementation from the standard library and is a growable and mutable UTF-8 encoded string type.
Many of String functions are like the ones from Vector.

## Creating String

`let mut s = String::new()`
or,
`let data = "initial content".to_string()`  
This will work on any type that has the `Display` trait.  
or,
`let s = String::from("some text")`

## Updating String

- Use the `+` operator or `format!` macro
- Also can use `push_str` to append text.
- `push` method takes a single char as param and appends it

```
let s1 = String::from("Hello, ");
let s2 = String::from("world!");
let s3 = s1 + &s2; // note s1 has been moved here and can no longer be used
```

Here, we add a reference of the second string to the first. We **cant add two String values together**. Internally, the `+` operator calls an `add` function which accepts &str as param (not &String). When we give it &String as param, it converts it using _deref coercion_ and is converted to a string slice like `&s2[..]`. The add function takes ownership of s1 and adds s2 to it, then returns ownership of the result which is more efficient than copying.

Phew!! That seemed so simple that I was going to ignore it, but I'm glad I read through. Docs are amazing.

Or, for multiple strings that we'd need to concat or if we dont want to give ownership, we can use the `format!` macro, which is kind of like `println!` but returns the String instead of printing.

```
    let s1 = String::from("tic");
    let s2 = String::from("tac");
    let s3 = String::from("toe");

    let s = format!("{}-{}-{}", s1, s2, s3);
```

## Indexing into Strings

- Indexing Strings using integers is not supported in Rust to prevent bugs.
- We can use String slicing to index, but if we do somestring[0..1] and the first character is actually 2 bytes long (like in some dialects), Rust will panic and throw an error.
- There are other methods to iterate over Strings given below
  - `chars` method can be used to get the value of each char.
  - `bytes` method will return value of each byte. (A unicode char can be made up of more than one byte so gotta be careful of that.)

# Hashmaps

Hashmaps can be used when we want to store data not by an index but by a name, such as, different teams scores in a sporting event.

## Creating hashmaps

Import using,  
`use std::collections::HashMap`  
create new hashmap using,  
`let mut scores = HashMap::new()`  
insert values using,  
`scores.insert(String::from("Blue"), 10)`

## Converting data into HashMap

If we have two vectors that have associated info, we can use `zip` to create a tuple that maps them and then use `collect` to convert it into a HashMap.

```
    use std::collections::HashMap;

    let teams = vec![String::from("Blue"), String::from("Yellow")];
    let initial_scores = vec![10, 50];

    let mut scores: HashMap<_, _> =
        teams.into_iter().zip(initial_scores.into_iter()).collect();
```

## Ownership

For owned vals like Strings, HashMaps take ownership. For values that have `copy` trait, hashmap makes a copy for itself.

## Accessing vals in HashMap

```
let team_name = String::from("Blue")
let score = scores.get(&team_name)
```

## Updating hashmap

- If we do `scores.insert(something_already_there, x)` then the old val will be replaced by new values.
- To insert only if old val doesnt exist, we use `scores.entry`, with the `.or_insert(50)` method. The return value of `entry` is an Enum that reps a val that might/not exist. The `or_insert(x)` returns a mutable reference to the corresponding key if exists, and if not, it inserts it and then returns a mutable ref to it.
- Updating based on old value can be done using the `entry` method above. For example:

```
for word in text.split_whitespace() {
        let count = map.entry(word).or_insert(0);
        *count += 1;
    }
```
