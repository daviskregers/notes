# Concurrency

One of the rusts major goal is to handle concurency safely and efficiently, where parts of program  are executed at the same time. By ownership and type checking, many concurency errors are thrown at the compile time.

## Concurrency and parallelism

In concurrency, suppose we have one CPU core and three processes that are being ran at the same time. The CPU will switch between these processes using an algorithm like Round Robin, saving the progress of it.

In parallelism, the CPU will have more than 1 core and it will be able to run more than 1 process at the same time while still using concurrency to switch between the processes.