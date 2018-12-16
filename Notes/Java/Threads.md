# [Return to Index](https://pizzastack.github.io)
# Threads
A *thread* is a unit of program execution that runs independently from other threads. Java programs can consist of multiple threads of execution that behave as if they were running on independent CPUs.

- `java.lang.Thread` is the Thread class representing a thread, which you can extend and then override its run() method. Afterwards, you call start().
- `java.lang.Runnable` is a functional interface (meaning only one method) which you can implement and then override run(). Afterwards, you can pass the object to a Thread instance and run start().
- The `synchronized` keyword is a modifier that can be used to write blocks of code, methods, or other resources to protect it in a multithreaded environment.
- `wait()` and `notify()` or `notifyAll()` methods of `java.lang.Object` can be used to suspend or wake up threads.

