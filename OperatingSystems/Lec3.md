# Lecture 3

## What are threads
A single unique execution context

A thread is in one of the following three states: 
- RUNNING — running 
- READY - eligible to run, but not currently running 
- BLOCKED - ineligible to run 

## pThreads
pThreads -> Posix threads
![image](https://github.com/mohsinarf/Notes/assets/69187532/1c9effc4-c878-4eb6-b704-30dbd59c823e)


### Non-determinism: 
- Scheduler can run threads in any order 
- Scheduler can switch threads at any time 
- This can make testing very difficult 
### Independent Threads 
- No state shared with other threads 
- Deterministic, reproducible conditions
### Cooperating Threads 
- Shared state between multiple threads 
### Goal: Correctness by Design 

## Locks
Locks provide two atomic operations: 
- **Lock.acquire()** — wait until lock is free; then mark it as busy 
- After this returns, we say the calling thread holds the lock 
- **Lock.release()** — mark lock as free 
- Should only be called by a thread that currently holds the lock 
- After this returns, the calling thread no longer holds the lock 

## Process management api
- exit — terminate a process
- fork — copy the current process
- exec — change the program being run by the current process
- wait — wait for a process to finish
- kill — send a signal (interrupt-like notification) to another proce:
- sigaction — set handlers for signals
## Creating Processes
### pid_t fork() — copy the current process 
- New process has different pid 
- New process contains a single thread 
### Return value from fork(): pid (like an integer) 
- When>0: 
  - Running in (original) Parent process 
  - return value is pid of new child 
- When = 0: 
  - Running in new Child process 
- When <0: 
  - Error! Must handle somehow 
  - Running in original process 
“+ State of original process duplicated in both Parent and Child! 
| — Address Space (Memory), File Descriptors (covered later), etc... 
## Conclusion
### Threads are the OS unit of concurrency 
- Abstraction of a virtual CPU core 
- Can use pthread create, etc., to manage threads within a process 
- They share data = need synchronization to avoid data races 
### Processes consist of one or more threads in an address space 
- Abstraction of the machine: execution environment for a program 
- Can use fork, exec, etc. to manage threads within a process 
### We saw the role of the OS library 
- Provide API to programs 
- Interface with the OS to request services 

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
