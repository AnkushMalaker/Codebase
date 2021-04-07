# Extensible Concurrency with the Sync and Send traits

Two concurrency concepts are embedded in the language: the std::marker traits Sync and Send.  
Send allows transferring ownership between threads.
Sync allows access from multiple threads.

> The Sync marker trait indicates that it is safe for the type implementing Sync to be referenced from multiple threads. In other words, any type T is Sync if &T (a reference to T) is Send, meaning the reference can be sent safely to another thread. Similar to Send, primitive types are Sync, and types composed entirely of types that are Sync are also Sync.
