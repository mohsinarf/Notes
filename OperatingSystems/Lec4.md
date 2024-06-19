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

   
 
