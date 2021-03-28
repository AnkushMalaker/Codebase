# Enums Basics

## Why/When?
Enums used when we have a limited number of possibilities and a value can have only ONE of those possibilities and not two or something. Like how an IP address can be either IPV4 or IPV6.  

## Defining and using enum  
Use `enum` Keyword. 
```
enum Ipkind{
    v4,
    v6
}
```

Use is like `let four = Ipkind::v4`  
We can define a function that takes an ipaddress and use Ipkind instead of just v4 or v6.  

We can give a type to the different kinds too, such that they hold values when enums are used. In the def above, we say `v4(String)` and then to use it to define an ipaddress, we do `let home = IpAddr::v4(String::from("127.0.0.1"))` (IpAddr is the ilpkind above, renamed to be semantically accurate now).  

Each variant can have a different type, for example, we can say v4(u8, u8, u8, u8)

## Nulls in rust
Nulls are problamatic and thus, rust has a different implementation of null. We have enum `Option<T>` which is defined in the standard library as having two fields:  
- `Some(T)`
- `None`

This is included in the prelude and doesnt need to be brought in meaning we can use `some` and `None` without the Option prefix. We need to tell the type of None though,  
`let absent_number: Option<i32> = None;` 


`<T>` is a generic parameter `Option<T>` is a different type. So we can't just add, say, `u32` to `Option<u32>`.  

