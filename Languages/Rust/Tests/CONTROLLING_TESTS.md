# Test Control

Tests are run parallely by default and outputs aren't shown.

## Parallel/Consecutive

To run tests **consecutively** or to specify `num_threads`, we can do it in the command line with the following argument:

`cargo test -- --test-threads=1`

The `--` seperator is used to separate args with the main command.

## Show fn outputs

`cargo test -- --show-output`

There's multiple ways to filter the test cases. Since I'm not studying for a test and the internet will not suddenly go down, I'll refer as needed from [here](https://doc.rust-lang.org/book/ch11-02-running-tests.html)
