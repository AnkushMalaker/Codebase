# Data to and between threads

## Using Data from main

We use the `move` closure for this.  
`let handle = thread::spawn(move ||{`

## Message Passing between threads

For this we use a channel. Channel has two parts:

- Transmitter
- Receiver

Channel is closed if either of them are dropped.

### Creating a channel

multiple producer single consumer - `mpsc::channel` - returns a transmitter and reciever.  
tx.send() sends a mesage
`rx.recv()` and `rx.try_recv()` recieves, difference being, `try_recv` doesn't send error signal and lets thread continue.

### Channels and ownership transference

Once a value is sent, it is no longer owned by the sender thread, so can't be referred.

### Multiple senders

This can be done by cloning the transmitter.
`let tx1 = tx.clone()`
