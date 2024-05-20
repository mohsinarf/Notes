# IPCs
Inter-process communication (IPC) refers to methods that allow processes to exchange data and coordinate actions. Here's an overview of the key IPC mechanisms in UNIX-like operating systems like Linux.

## 𝗣𝗶𝗽𝗲𝘀

Pipes connect the input and output of two or more processes, creating a pipeline for streaming data. For example, shell scripts routinely chain together commands using the pipe operator:

cat /var/log/syslog | grep 'error' | less

## 𝗠𝗲𝘀𝘀𝗮𝗴𝗲 𝗤𝘂𝗲𝘂𝗲𝘀

Message queues provide asynchronous communication by enabling processes to exchange data in the form of messages. Messages written to a queue are handled in the first-in, first-out order. For instance, a server may dispatch jobs to queues which worker daemons pull from and process independently.

## 𝗦𝗶𝗴𝗻𝗮𝗹𝘀

Signals provide a notification system that allows processes to be immediately alerted of important events like being forcibly terminated. For example, SIGKILL provides a reliable way to end non-responsive applications.

## 𝗦𝗲𝗺𝗮𝗽𝗵𝗼𝗿𝗲𝘀

Semaphores help synchronize access to resources that need to be shared between processes by limiting concurrent usage. They help avoid race conditions from processes simultaneously reading and writing to resources like shared data files.

## 𝗦𝗵𝗮𝗿𝗲𝗱 𝗠𝗲𝗺𝗼𝗿𝘆

Shared memory allows direct access to shared memory areas so multiple processes can read and modify data efficiently without copying. An example use case is a program that manipulates a large image frame, where multiple processes can access and process different parts of the image simultaneously.
