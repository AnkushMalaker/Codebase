# Control Flow

## If else

The if statements need a `bool` in their condition, so something like, if (number) that evealuates to 3 will throw an error.

We can use if in a let statement as follows:  
`let condition = true;`
`let number = if condition {5} else {7}`

## Loops

Simple infinite loop can be done usnig `loop` keyword.

We can get values out of a loop as such:

```
let mut counter = 0;

    let result = loop {
        counter += 1;

        if counter == 10 {
            break counter * 2;
        }
    };
```

The value used with the break keyword is returned as the result of the loop.

### While/For

The while loop is slower than for because it adds a conditional statement to check during runtime. Its better to use a for loop to iterate over elements.

```
let a = [10, 20, 30, 40, 50];

    for element in a.iter() {
        println!("the value is: {}", element);
    }
```

This ensures no bugs for out of index or under indexing.

For a for loop, we can use a `range`. Or, the reverse of a range called `rev`.

```
fn main() {
    for number in (1..4).rev() {
        println!("{}!", number);
    }
    println!("LIFTOFF!!!");
}
```
