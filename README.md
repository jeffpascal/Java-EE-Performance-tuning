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
  - The heap storage for objects is reclaimed by an automatic storage management system. The heap may be of a fixed or dynamic size, and the memory allocated for the heap area does not need to be contiguous

- METHOD AREA AND RUNTIME CONSTANT POOL
  - The method area is analogous to the storage area for the compiled code of a conventional language or to the text segment in an operating system process. It stores per-class structures such as the runtime constant pool; field and method data; the code for methods and constructors, including the special methods used in class, instance, and interface initialization.

The method area is created on the virtual machine startup. Although it is logically a part of the heap, it can or cannot be garbage collected, and it can be of a fixed or dynamic size.

It also contains a runtime constant pool, which is a per-class or per-interface runtime representation of the constant_pool table in the class file. It contains several kinds of constants, ranging from numeric literals known at the time of compiling, to method and field references that must be resolved at runtime.

The runtime constant pool serves a function similar to that of a symbol table for a conventional programming language, although it contains a wider range of data than a typical symbol table.

- JVM STACK
  - Each of the JVM threads has a private stack created at the same time as that of the thread. The stack stores frames and is analogous to the stack of a conventional language (such as C). It holds local variables and partial results and plays a part in the method invocation and return. Because this stack is never manipulated directly, except to push and pop frames, the frames may be heap allocated. Similar to the heap, the memory for this stack does not need to be contiguous.

This specification permits that stacks can be either of a fixed or dynamic size. If it is of a fixed size, the size of each stack may be chosen independently when that stack is created.

- NATIVE METHOD STACKS (C STACKS)
Native method stacks is called C stacks; it support native methods (methods written in a language other than the Java programming language), typically allocated per each thread when each thread is created.

The size of native method stacks can be either fixed or dynamic.

- PC REGISTERS
  - Each of the JVM threads has its own program counter (pc) register. At any point, each of the JVM threads is executing the code of a single method, namely the current method for that thread.

  - As the Java applications can contain some native code (for example, using native libraries), we have two different ways for native and nonnative methods. If the method is not native (that is, a Java code), the PC register contains the address of the JVM instruction currently being executed. If the method is native, the value of the JVM's PC register is undefined.
