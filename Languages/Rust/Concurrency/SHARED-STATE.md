# Shared-State Concurrency

Another way of handling concurrency.

## Mutex to allow multiple threads to access same data

Mutex is part of the `std::sync::Mutex` crate.
It is a smart pointer. Mutex.lock() returns a smart pointer called `MutexGuard` wrapped in a LockResult.

### Syntax of mutex

1. Creatie using the new() method.
2. To access data inside, we have to use `let mut ref = m.lock().unwrap()`.
   If the lock is acquired, ref will be a mutable ref to the data inside it. If it fails (ie, if some other thread has acquired the lock), it will throw error.
3. Once it goes out of scope, the lock will be given back to m.

When giving a mutex to threads, rust will throw error due to multiple ownerships.  
`Rc<T>` can't be passed b/w threads since it doesn't use concurrency primitives to prevent intteruptions to change by different threads leading to possibility of wrong outputs.  
Thus we use `Arc<T>` which is atomic reference counting. Atomics are another type of concurrency prmitive.
