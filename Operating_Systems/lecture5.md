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

## Connection setup over Tcp/Ip
![image](https://github.com/mohsinarf/Notes/assets/69187532/67fe86cb-f7dc-4a72-a0f6-a06f69d1e6e6)

## Sockets with concurrency, with protection
![image](https://github.com/mohsinarf/Notes/assets/69187532/fea8ea37-f34b-4a1e-af0d-cbc5b2193512)

## Sockets with concurrency, without protection
![image](https://github.com/mohsinarf/Notes/assets/69187532/36951671-b72c-46ee-ac8c-9f862e3f59bc)

## Thread pool
![image](https://github.com/mohsinarf/Notes/assets/69187532/30579d78-7c87-4d20-8d92-efe756f10198)

## Conclusion
![image](https://github.com/mohsinarf/Notes/assets/69187532/7f7f884f-1d02-4c66-a08f-1c7d4b300f5c)

  ## Port vs socket
