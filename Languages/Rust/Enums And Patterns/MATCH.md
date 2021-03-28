# Match control flow  

## Match syntax and use
Think of match as a coin sorting machine with coins rolling down series of holes (match conditions).  
The conditions in match are called match arms. An arm has two parts: a pattern and some code separated by `=>`.  
```
fn value_in_cents(coin: Coin) -> u8 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter(state) => {
            println!("State quarter from {:?}!", state);
            25
        }
    }
}
```

## Match can bind to values
(In code above) we can call `value_in_cents(Coin::Quarter(UsState::Alaska))` to get the print statement from it. (UsState is an enum with alaska as one of the possible values).  

## Matches are exhaustive
Matches are also exhaustive and will give a compile time error if we don't cover all cases

The `_` Placeholder is like the "else" or "default" case in a switch case. 

