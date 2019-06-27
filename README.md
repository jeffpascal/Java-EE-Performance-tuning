# Java-EE-Performance-tuning
My notes on Java Performance Tuning


### Synchronous vs Asynchronous execution
- When you execute something synchronously, you wait for it to finish before moving on to another task. When you execute something asynchronously, you can move on to another task before it finishes.
- in the context of computers, this translates into executing a process or task on another "thread".
- **At its core (pardon the pun), a processor can simply execute a command, it has no concept of doing two things at one time. The operating system simulates this by allocating slices of time to different threads.**
- on multiple cores, things can happen at the same time. The operating system can allocate time to one thread on the first processor, then allocate the same block of time to another thread on a different processor.
