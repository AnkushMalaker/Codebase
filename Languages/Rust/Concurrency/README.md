# Concurrency

Threads done in two ways:

1. 1:1 using API provided by the operating system (Given by rust)
2. M:N by green thread languages. (Has larger runtime to manage threads, can be implemented by using crates in rust).

## Creating threads

`thread` is part of standard library.  
We use `thread::spawn` for new thread.  
`thread::sleep` force a thread to stop its execution for a short duration, allowing a different thread to run.

## Waiting for all threads to finish using `join`

If main prog code finishes before all threads finish they will just be ended prematurely.  
Return type of `thread::spawn` is `JoinHandle`. To let a set of threads finish exec before quitting program we do this:

```
let handle = thread::spawn(||{
for i in 1..10{
//code
}
});

//main program code

handle.join().unwrap();
```

## Using Data with threads

We use the `move` closure for this.  
`let handle = thread::spawn(move ||{`

# Message Passing
