# References and borrowing

Passing a variable to a function makes the variable move into the fucntions scope. To avoid this, we can pass it as a return value.

Instead, we can use reference to the object as the parameter:  
`let len = calculate_length(&s1)`
This will allow s1 to be used after the function call. Consequently, we will have to accept a reference in the function definition also.

```
fn calculate_length(s: &String) -> usize {
	s.len()
}
```

The opposite of referencing is dereference which uses the \* operator.

References are immutable by default. So if we were to change s in the above example, we'd need to declare s as mutable and accept a mutable reference with `&mut String`
To prevent data races, with mutable references, one piece of data in a scope can only have one mutable reference at a time.

## Dangling references

Basically a reference to a memory place that's assigned to something else.  
Rust prevents this during compile time. In cases where we need it, just return the string/value instead of returning the reference.

## Reference rules:

- At any given time, you can have either one mutable reference or any number of immutable references.
- References must always be valid
