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

## How a program runs
![image](https://github.com/mohsinarf/Notes/assets/69187532/bf2734bd-889e-49fc-b7e4-bba3bd322700)

## Instruction Fetch/Decode/Execute
![image](https://github.com/mohsinarf/Notes/assets/69187532/24f6dde7-c3b2-4a73-8687-8dff087fc577)

## Illusion of multiple processors
![image](https://github.com/mohsinarf/Notes/assets/69187532/dca13033-bd4d-4a2f-af79-237c1c8cbb60)

### Thread Control Block (TCB)
- Holds contents of registers when thread not running 

**Where are TCBs stored?**
- For now, in the kernel 

## OS Abstractions 
- Processor —> Thread
- Memory —> Address Space
- Disks, SSDs, ... —> Files
- Networks —> Sockets
- Machines —> Processes
  

## Address Space

## Simple Proctection: Base and Bound




## Links
- https://www.youtube.com/watch?v=4FpG1DcvHzc&t=1256s
