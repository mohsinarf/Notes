# Lecture 3

## What are threads


## Multiprocessing vs Multiprogramming vs Multithreading

| Feature          | Multiprocessing                                   | Multiprogramming                                | Multithreading                                   |
|------------------|---------------------------------------------------|-------------------------------------------------|-------------------------------------------------|
| **Definition**   | Use of two or more CPUs within a single system    | Multiple programs loaded in memory, executed by one CPU | Multiple threads within a single process managed by one CPU |
| **Key Concept**  | Parallel execution of processes                   | CPU switching between programs                  | Independent threads sharing the same process memory |
| **Parallelism**  | True parallelism with multiple CPUs               | No true parallelism, only concurrency           | Concurrency on a single CPU, parallelism on multi-core CPUs |
| **Isolation**    | High (each process in its own memory space)       | Moderate (separate programs)                    | Low (threads share the same memory space)         |
| **Context Switching** | Relatively heavy (between processes)           | Moderate (between programs)                     | Lightweight (between threads)                     |
| **Memory Management** | Each process has its own memory               | Efficient memory management needed              | Threads share the same memory                     |
| **Hardware Requirement** | Multiple CPUs or cores                      | Single CPU                                      | Single CPU (for concurrency), multi-core CPU (for parallelism) |
| **Example Use Cases** | High-performance computing, server applications | Early operating systems, batch processing systems | Web servers, GUI applications, real-time systems |
