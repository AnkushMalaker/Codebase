# Unrecoverable errors

When this happens,  the panic! macro is used and it unwinds(clears stack) and then exits. If we wanna change that then we can put (to make binary small or whatever)
```
[profile.release]
panic = 'abort'
```
in our toml file. The os will have to clean up that memory then. 

## Using panic! 
Simply use `panic!("Message")` macro and the program will exit with message when it reaches that line.  

## panic! Backtrace
It twlls us the original place that caused the panic, which can be in some library and not on our file. To fix, we can call `RUST_BACKTRACE=1 cargo run` to see traceback.

