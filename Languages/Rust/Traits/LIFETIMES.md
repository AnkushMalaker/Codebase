# Lifetimes

Used to give a lifetime to a reference so it doesn't dangle.  
Usually inferred, but if multiple lifetimes poss, have to explicitely mention, life types.

This only tells Rust how lifetimes of objects relate to each other. If two itesm have `'a` as their lifetime, they will both live as long as their generic lifetime.

## Syntax

The name of lifetime starts with `'` and name is usually lowercase and short. They're placed after the `&`.

## Lifetime annotation in function sig

Like generic params, we define lifetime param within `<>`. Example:

```
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}
```

> The function signature now tells Rust that for some lifetime `'a,` the function takes two parameters, both of which are string slices that live at least as long as lifetime `'a.` The function signature also tells Rust that the string slice returned from the function will live at least as long as lifetime `'a.` In practice, it means that the lifetime of the reference returned by the longest function is the same as the smaller of the lifetimes of the references passed in.

## Lifetime annotations in structs

It’s possible for structs to hold references, but in that case we would need to add a lifetime annotation on every reference in the struct’s definition.

## lifetime elision rules

All the lifetime rules that rust infers is becasue its programmed into rust code. This can improve overimte when more deterministic rules for these lifetimes get discovered.

> Lifetimes on function or method parameters are called input lifetimes, and lifetimes on return values are called output lifetimes.
> The compiler uses three rules to figure out what lifetimes references have when there aren’t explicit annotations. The first rule applies to input lifetimes, and the second and third rules apply to output lifetimes. If the compiler gets to the end of the three rules and there are still references for which it can’t figure out lifetimes, the compiler will stop with an error. These rules apply to fn definitions as well as impl blocks.

Check the [docs](https://doc.rust-lang.org/book/ch10-03-lifetime-syntax.html) to see exact rules.
