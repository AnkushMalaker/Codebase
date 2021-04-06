# Iterators

- Iterators in rust are **lazy**.
- All iterators impl a trait names Iterator.
- The Iterator trait only requires implementors to define one method: the next method, which returns one item of the iterator at a time wrapped in `Some` and, when iteration is over, returns `None.`
- Iterators need to be mutable because calling `.next()` changes the internal state of the iterator.

## Methods that Consume the Iterators

- Methods that call `next` are called _consuming adaptors_.
  They consume adaptors. (duh!)

## Methods that produce other iterators

For example, `v1.iter().map(|x| x + 1);` would not do anything because it returns an iterator. This will need to be consumed using `collect`.  
Note, map takes a closure so we can specify any operation there :)

## Using Closures that Capture Their Environment

The filter, we can do something like:  
`shoes.into_iter().filter(|s| s.size == shoe_size).collect()`

## Defining our own iterator [here](https://doc.rust-lang.org/book/ch13-02-iterators.html#creating-our-own-iterators-with-the-iterator-trait)
