# Traits

Traits are similar to interfaces.

## Defining Trait

Trait definitions are a way to group method signatures together to define a set of behaviors necessary to accomplish some purpose.

```
pub trait Summary{
fn summarize(&self) -> String;
}
```

Summary is trait name and summarize is the method signature. Instead of defining it we just close it with semicolon.

## Implementing trait on a Type

```
impl Summary for NewsArticle {
    fn summarize(&self) -> String {
        format!("{}, by {} ({})", self.headline, self.author, self.location)
    }
}
```

NewsArticle is a struct with headline, author etc as its variables.  
To define it over another struct, we have to do the same as above and chane the `fn` accordingly.

We can simply call this like `NewsArticle.summarize()` since its all in the same scope. If we make a crate called aggregator, we'd need to bring it in scope like `use aggregator::Summary`. Summary would need to be a public trait which is why we used the `pub` keyword there.

## Limitations

- Can't impliment external trait on external type. Like `Display` trait on `Vec<T>` within out `aggregator.`
- This is because of coherence, specifially, orphan rule. [mode](https://doc.rust-lang.org/book/ch10-02-traits.html#implementing-a-trait-on-a-type)

## Default implementations

To specify a default implementation, we define it in the `trait` instead of leaving it blank/ending it with a semicolon. Then, to use default implementations, we specify an empty `impl` block with `impl Summary for NewsArticle }{}`.

Default implementations can call other methods of the same trait.

## Traits as parameters

`impl Trait`
We can use a trait as param in a function, such that it will accept any type that implements that trait.

```
pub fn notify(item: &impl Summary) {
    println!("Breaking news! {}", item.summarize());
}
```

`item: &impl Summary` actaully stands for <T: Summary>(item: &T)

We can employ notify to use **multiple trait bonds** using the `+` operator.  
`pub fn notify(item: &(impl Summary + Display)){`
or on generic types like:  
`pub fn notify<T: Summary + Display>(item: &T) {`

## `Where` clause

This is easier syntax to mention trait bounds for a function, ie, "allow this function to take all types that apply these traits.".

So, this:
`fn some_function<T: Display + Clone, U: Clone + Debug>(t: &T, u: &U) -> i32 {`  
can be written as:

```
fn some_function<T, U>(t: &T, u: &U) -> i32
    where T: Display + Clone,
          U: Clone + Debug
{
```

## Returning types that implement traits

Similar to using traits as parameters, using `imp <trait name>` implies function will return some type that implements that trait.

[Read again whenever you can :D](https://doc.rust-lang.org/book/ch10-02-traits.html#clearer-trait-bounds-with-where-clauses)
