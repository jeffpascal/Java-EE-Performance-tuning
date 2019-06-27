# Java-EE-Performance-tuning
My notes on Java Performance Tuning


### Synchronous vs Asynchronous execution
- When you execute something **synchronously**, you wait for it to finish before moving on to another task. When you execute something **asynchronously**, you can move on to another task before it finishes.
- in the context of computers, this translates into executing a process or task on another "thread".
- **At its core (pardon the pun), a processor can simply execute a command, it has no concept of doing two things at one time. The operating system simulates this by allocating slices of time to different threads.**
- on multiple cores, things can happen at the same time. The operating system can allocate time to one thread on the first processor, then allocate the same block of time to another thread on a different processor.

### Understanding memory structure in the JVM
- Understanding the memory structure in the JVM is essential to tune the JVM for the better performance of the Java applications, so the essential knowledge to deal with the JVM in general, and in particular, the JVM memory management is required and expected from a performance tuning expert to master.

- Client Virtual Machine
  - The client virtual machine is tuned to reduce the startup time and memory footprint.
- Server virtual Machine
  - This virtual machine is designed to maximize program execution speed. It can be invoked by using the -server command-line option when launching the application.
  
- Heap Area
  - The heap area represents the runtime data area, from which the memory is allocated for all class instances and arrays, and is created during the virtual machine startup.
