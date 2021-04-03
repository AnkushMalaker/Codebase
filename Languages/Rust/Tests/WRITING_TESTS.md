# Basics

A test checks non-test code to see if its doing what its supposed to.  
It does three things:

1. Set up any needed data or state.
2. Run the code you want to test.
3. Assert the results are what you expect.

To test fn, put `#[test]` above the `fn` in a function. Doing `cargo test` would build a test binary to test all functions annotated with the above.

## `assert!` macro

It calls `panic!` macro if the assertion is `false`.

## Equality with `assert_eq!` and `assert_ne!`

Same as doing `x==y` and passing that to `assert!`.  
eq is for equality and ne for not equal.

## Custom faliure messages

`assert!(checking_thing, "Message");`

## Should panic!

We can check if a value that should make program panic is infact making program panic by putting `#[should_panic]` over the test function.
The message isn't very helpful and this can be **impercise** cuz it will pass even if program panics because of some other reason.  

To counteract that, we add an `expected` param to `should_panic`. Ex:  
`#[should_panic(expected = "Guess value must be less than or equal to 100")]`  


