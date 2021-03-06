## Multithreading and multiprocessing
use `threading` if your program is network bound / IO or `multiprocessing` if it's CPU bound

### Process

A process is an instance of a computer program being executed. Each process has its own memory space it uses to store the instructions being run, as well as any data it needs to store and access to execute.

### Threads

Threads are components of a process, which can run parallely. There can be multiple threads in a process, and they share the same memory space, i.e. the memory space of the parent process. This would mean the code to be executed as well as all the variables declared in the program would be shared by all threads.

### Deadlock
Overusing mutex locks also has a downside - it can introduce deadlocks in the program. A deadlock is a state when a thread is waiting for another thread to release a lock, but that other thread needs a resource to finish that the first thread is holding onto. This way, both of the threads come to a standstill and the program halts. Deadlock can be thought of as an extreme case of starvation. To avoid this, we have to be careful not to introduce too many locks that are interdependent.

### GIL
`GIL`, or the Global Interpreter Lock - protects access to Python objects, preventing multiple threads from executing Python bytecodes at once.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA0NDA5MjA4M119
-->