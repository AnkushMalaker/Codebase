# If let

Simple to understand from the syntax. It's just a more convenient way to do matching with lesser code:

```
let mut count = 0;
    match coin {
        Coin::Quarter(state) => println!("State quarter from {:?}!", state),
        _ => count += 1,
    }
```

If let equivalent:

```
let mut count = 0;
    if let Coin::Quarter(state) = coin {
        println!("State quarter from {:?}!", state);
    } else {
        count += 1;
    }
```

The `if let` construct reads: "if `let` destructures `coin` into
// `Coin::Quarter(state)`, evaluate the block (`{}`).
