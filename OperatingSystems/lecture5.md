# Abstraction 3: IPC, Pipes and Sockets


## Protocol
  A protocol is an agreement on how to communicate ~~
- **Includes**
  - Syntax: how a communication is specified & structured 
    - Format, order messages are sent and received 
  - Semantics: what a communication means 
    - Actions taken when transmitting, receiving, or when a timer expires
- Described formally by a state machine 

## What is a network connection?
- Bidirectional stream of bytes between two processes on possibly different machines 

- Abstractly, a connection between two endpoints A and B consists of: 
  - A queue (bounded buffer) for data sent from A to B 
  - A queue (bounded buffer) for data sent from B to A

 ## Sockets
- An abstraction for one endpoint of a network connection
-  Sockets: Endpoint for Communication 
  - Queues to temporarily hold results
    
- Looks just like a file with a **file descriptor** 
  - Corresponds to a network connection (two queues) 
  - write adds to output queue (queue of data destined for other side) 
  - read removes from it input queue (queue of data destined for this side) 
  - Some operations do not work, e.g. 1seek   
   

  ## Port vs socket
