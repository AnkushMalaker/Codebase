# Test Organizatoin

Tests:

1. Unit (small, focused)
2. Integratoin (entirely external)

## 1. Unit Tests

Convention is to create a module named tests in each file to contain the test functions and to annotate the module with cfg(test).

Adding #[cfg(test)] tells rust compiler to avoid that module from build and only run it when cargo test is called. Integratoin tests don't need this.

## 2. Integratoin Tests

Create a tests directory at the top level of our project directory, next to src.

```
use adder; //Bring in the module we want to test

#[test]  //defines that its a test
fn it_adds_two() {
    assert_eq!(4, adder::add_two(2));
}

```

This will do integration, unit and doc test together.  
To only do integeration test, use `cargo test --test integeration test`
