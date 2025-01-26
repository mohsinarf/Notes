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
  

## Second OS concept: Address Space
- For 32-bit processor: 2°2 = 4 billion addresses
- For 64-bit processor: 2% = 18 quantillion addresses
![image](https://github.com/mohsinarf/Notes/assets/69187532/1c874749-9b2c-4c35-b5be-0d278b4a713a)

## Simple Proctection: Base and Bound
![image](https://github.com/mohsinarf/Notes/assets/69187532/d4ebfde3-11fd-4215-86da-ca66b8ce5d33)

### Paged Virtual Address
A **page table** is a data structure used in virtual memory management to map virtual addresses to physical addresses
## Third OS Concept: Process

## Third OS concept: Process
-  **Definition**: execution environment with Restricted Rights 
   - (Protected) Address Space with One or More Threads 
   - Owns memory (address space) 
   - Owns file descriptors, file system context, ... 
   - Encapsulate one or more threads sharing process resources 
- Application program executes as a process 
  - Complex applications can fork/exec child processes [later!] 
- Why processes? 
  - Protected from each other! 
  - OS Protected from them 
  - Processes provides memory protection
- Fundamental tradeoff between protection and efficiency 
  - Communication easier within a process 
  - Communication harder between processes

 ### Why Do We Need Processes?? 
- Reliability: bugs can only overwrite memory of process they are in 
- Security and privacy: malicious or compromised process can’t read or write other process’ data 
- (to some degree) Fairness: enforce shares of disk, CPU 
### Mechanisms: 
- Address translation: address space only contains its own data 
- BUT: why can’t a process change the page table pointer? 
    - » Or use I/O instructions to bypass the system? 
- Hardware must support privilege levels 
    
![image](https://github.com/mohsinarf/Notes/assets/69187532/17cba2f4-f594-4448-8d84-6fb1c07a44c5)

## Fourth OS Concepts: Dual Mode Operation
![image](https://github.com/mohsinarf/Notes/assets/69187532/a616bef3-a1dc-458b-aba1-006ee3e463df)
![image](https://github.com/mohsinarf/Notes/assets/69187532/3219bdc4-e9bc-4379-b931-28e597cb9b94)

![image](https://github.com/mohsinarf/Notes/assets/69187532/7f57debc-2720-4e59-a966-95043370bbba)
![image](https://github.com/mohsinarf/Notes/assets/69187532/b954bd3c-ec17-49e0-8ef2-5fcd5a1a0d33)

## Links
- https://www.youtube.com/watch?v=4FpG1DcvHzc&t=1256s
