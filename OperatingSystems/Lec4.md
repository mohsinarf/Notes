# Lec4: Abstractions: Files and I/O

## Semaphores
- Semaphores are a kind of **generalized lock**
  - First defined by Dijkstra in late 60s 
  - Main synchronization primitive used in original UNIX (& Pintos) 
- Definition: a Semaphore has a non-negative integer value and supports the following two operations: 
  - P() or down(): atomic operation that waits for semaphore to become positive, then decrements it by 1 
  - V() or up(): an atomic operation that increments the semaphore by 1, waking up a waiting P, if any 

- P() stands for “proberen” (to test) and V() stands for “verhogen” (to increment) in Dutch
