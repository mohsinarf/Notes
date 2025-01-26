# Lec4: Abstractions: Files and I/O

## Semaphores
- Semaphores are a kind of **generalized lock**
  - First defined by Dijkstra in late 60s 
  - Main synchronization primitive used in original UNIX (& Pintos) 
- Definition: a Semaphore has a non-negative integer value and supports the following two operations: 
  - P() or down(): atomic operation that waits for semaphore to become positive, then decrements it by 1 
  - V() or up(): an atomic operation that increments the semaphore by 1, waking up a waiting P, if any 

- P() stands for “proberen” (to test) and V() stands for “verhogen” (to increment) in Dutch

## pThread


## File System Abstraction
- High-Level File I/O: Streams
- Low-Level File I/O: File Descriptors
- How and Why of High-Level File I/O
- Process State for File Descriptors
- Common Pitfalls with OS Abstractions [if time]

### File
- Named collection of data in a file system 
- POSIX File data: sequence of bytes 
  - Could be text, binary, serialized objects, ... 
- File Metadata: information about the file 
  - Size, Modification Time, Owner, Security info, Access control 
### Directory 
- “Folder” containing files & directories 
- Hierachical (graphical) naming 
  - Path through the directory graph 
  - Uniquely identifies a file or directory 
    - /home/ff/cs1 62/public_html/fa14/index.html

![image](https://github.com/mohsinarf/Notes/assets/69187532/4ac9b647-2de4-4380-8712-c1e90b721536)

## Key Unix I/O Design Concepts
![image](https://github.com/mohsinarf/Notes/assets/69187532/cf31699c-fb42-4613-bba5-0d488d6eb9ec)

![image](https://github.com/mohsinarf/Notes/assets/69187532/6f354beb-8819-49f9-8562-e1919079c7e9)

## High-Level vs Low Level File Api
![image](https://github.com/mohsinarf/Notes/assets/69187532/c050ec95-4a63-47a6-bc7a-3bcfff6cdfeb)

### What's in the FILE* returned by fopen?
- File descriptor (from call to open) <= Need this to interface with the kernel!
- Buffer (array)
- Lock (in case multiple threads use the FILE concurrently)

### FILE Buffering
- When you call furite, what happens to the data you provided?
- It gets written to the FILE's buffer 
- If the FILE’s buffer is full, then it is flushed 
    - Which means it's written to the underlying file descriptor 
- The C standard library may flush the FILE more frequently 
    - e.g., if it sees a certain character in the stream 
- When you write code, make the weakest possible assumptions about how data is flushed from FILE buffers 

 ![image](https://github.com/mohsinarf/Notes/assets/69187532/069e4118-e34e-4625-abe8-96496ba29421)

### State maintained by Kernel
![image](https://github.com/mohsinarf/Notes/assets/69187532/71ab7b21-b32d-47da-8343-7257f9988aeb)

