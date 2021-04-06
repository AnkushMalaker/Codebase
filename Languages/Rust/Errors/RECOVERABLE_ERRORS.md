# Recoverable Errors

We use the `Result<T,E>` type which is an enum with two fields, namely, OK(T) and Err(E) to handle recoverable errors.

Example on how to use it:

```
fn main() {
    let f = File::open("hello.txt");

    let f = match f {
        Ok(file) => file,
        Err(error) => panic!("Problem opening the file: {:?}", error),
    };
}
```

## Matching different kind of errors

We can use match with `error.kind()` which will return things like `ErrorKind::NotFound`.  
We can more elegantly use closures which we will come to later.

## Shortcuts for the above

The `.unwrap()` method does what we did with the match statement. Returns inner val if ok, panic! if not.  
Similarly, we can add `.expect("message on fail")` and that'll show the message along with the unwrap functionality.

## Propogating error

We can return a `Result<String, io::Error>` (for example) to return an error to the program that's calling the function. This way it'll be easier to solve.

This, for example:  
let f = File::open("hello.txt");

```
    let mut f = match f {
        Ok(file) => file,
        Err(e) => return Err(e),
    };

    let mut s = String::new();

    match f.read_to_string(&mut s) {
        Ok(_) => Ok(s),
        Err(e) => Err(e),
    }
```

There is a shortcut for the same, the `?` Operator.

```
    let mut f = File::open("hello.txt")?;
    let mut s = String::new();
    f.read_to_string(&mut s)?;
    Ok(s)
```

It words diff than the match statements above. See [this](https://doc.rust-lang.org/book/ch09-02-recoverable-errors-with-result.html) for more.

This can also be chained.

```
    let mut s = String::new();

    File::open("hello.txt")?.read_to_string(&mut s)?;

    Ok(s)
```
