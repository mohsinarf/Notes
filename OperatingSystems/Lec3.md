# Lecture 3

## What are threads
A single unique execution context

A thread is in one of the following three states: 
- RUNNING — running 
- READY - eligible to run, but not currently running 
- BLOCKED - ineligible to run 

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



# Amdahl's Law

Amdahl's Law is a formula used to find the maximum improvement in the performance of a system when only part of the system is improved. It was proposed by computer scientist Gene Amdahl in 1967, primarily to address the limits of parallel computing. The law highlights that the performance gains from parallelizing a portion of a task are limited by the portion that cannot be parallelized.

## Formula

Amdahl's Law is mathematically expressed as:

\[ S = \frac{1}{(1 - P) + \frac{P}{N}} \]

where:
- \( S \) is the overall speedup of the task.
- \( P \) is the proportion of the task that can be parallelized.
- \( N \) is the number of processors or cores.
- \( (1 - P) \) is the proportion of the task that must remain serial.

## Conclusion

Amdahl's Law is crucial for understanding the limits of parallel processing and optimizing system performance. It emphasizes the importance of minimizing the serial portion of tasks to achieve significant performance improvements through parallelism.


## Link
- https://www.youtube.com/watch?v=QSep-J6vtdc&list=PLF2K2xZjNEf97A_uBCwEl61sdxWVP7VWC&index=3&ab_channel=JohnKubiatowicz
