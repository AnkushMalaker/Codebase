# Slice type

String slices take reference to a string section. We declare them like this:

```
let s = String::from("Hello");
let hell = &s[0..4];
```

With the `..` syntax, we can just ommit the first number if we want it from start, omit last if we want it till end or omit both if we want whole string.
