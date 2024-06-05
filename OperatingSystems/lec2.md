# Lecture no 2

## Four fundamentals of OS concepts
### Thread: Execution Context 
- Fully describes program state 
- Program Counter, Registers, Execution Flags, Stack 
### Address space (with or w/o translation) 
- Set of memory addresses accessible to program (for read or write) 
- May be distinct from memory space of the physical machine (in which case programs operate in a virtual address space) 
### Process: an instance of a running program 
- Protected Address Space + One or more Threads 
### Dual mode operation / Protection 
- Only the “system” has the ability to access certain resources 
- Combirted with translation, isolates programs from each other and the OS from programs 

## OS Abstractions 
- Processor —> Thread
- Memory —> Address Space
- Disks, SSDs, ... —> Files
- Networks —> Sockets
- Machines —> Processes
  
### Thread Control Block (TCB)

## Address Space

## Simple Proctection: Base and Bound




## Links
- https://www.youtube.com/watch?v=4FpG1DcvHzc&t=1256s
