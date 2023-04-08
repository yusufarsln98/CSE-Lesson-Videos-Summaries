# CSE344 - 6th Week

# [00:00:02](https://youtu.be/R3yDioKEUG8?t=2s) Introduction

This video is about inter-process communication (IPC) and focuses on pipes and fifos. The speaker also briefly mentions other IPC tools such as shared memory, signals, semaphores, file locks, condition variables, and mutexes.

## [00:04:07](https://youtu.be/R3yDioKEUG8?t=247s) Pipes and Fifos

- Pipes are used for communication between a process and its related parent or between threads in the same process.
- Fifos (also known as named pipes) enable communication between processes that are not related.
- Sockets allow computers from different domains to communicate with each other.
- Pipes and fifos are sequential communication devices used for data transfer.

## [00:08:19](https://youtu.be/R3yDioKEUG8?t=499s) Synchronization Tools

- Semaphores are integers used to synchronize processes or threads.
- File locks are an old way of synchronization supported by the kernel but do not have a specific database entry.
- Mutexes, monitor or condition variables can solve most synchronization issues but have some limitations.

# Conclusion

This video provides an overview of IPC tools with a focus on pipes and fifos. It also briefly mentions other synchronization tools such as semaphores, file locks, mutexes, monitor or condition variables.

# [0:10:12](https://youtu.be/R3yDioKEUG8?t=612s) Introduction to Pipes

In this section, the speaker introduces pipes and explains how they are used to communicate between two threads in a single process or a parent and a child.

- A pipe is like a pipe in real life where one side writes and sends it through the pipe while the other side receives it.
- Pipes are typically used to communicate between two threads in a single process or a parent and a child.

# [0:11:02](https://youtu.be/R3yDioKEUG8?t=662s) How Pipes Work

The speaker explains how pipes work using an example of sending output from one command to another using the `|` character.

- The `|` character is called the pipe symbol, which takes the output of standard output of one command and puts it into the pipe as standard input for another command.
- The `wc` command stands for word count, which displays how many characters, words, and lines that file or input has.
- Pipes can also be generated inside programs using similar representations.

# [0:13:00](https://youtu.be/R3yDioKEUG8?t=780s) Limitations of Pipes

The speaker discusses some limitations of pipes when communicating between two processes.

- The capacity of pipes is limited. If one side writes too fast and the other cannot consume that much data, then either writer or reader will be blocked until data becomes available.
- This blocking property can be used for synchronization between processes by removing either the input or output part of it.

# [0:14:34](https://youtu.be/R3yDioKEUG8?t=874s) Creating Pipes Inside Programs

The speaker explains how to create pipes inside programs using file descriptors.

- Two file descriptors are needed, one for reading and the other for writing.
- If using pipes between a child and parent process, one process should remove the input part while the other removes the output part to make communication one directional.

# [0:15:26](https://youtu.be/R3yDioKEUG8?t=926s) Two-Way Communication with Pipes

The speaker explains how two-way communication can be achieved with pipes but warns that synchronization is not easy.

- A common practice is for one process to remove either the input or output of it and the second process to remove the reverse part of it so that communication becomes one directional.
- If a child needs to send data back to its parent, then another pipe can be created in reverse.

# [0:17:41](https://youtu.be/R3yDioKEUG8?t=1061s) Synchronization and Pipes

In this section, the speaker discusses synchronization and pipes in multi-process programs. They recommend using synchronization to manipulate what is going on with the system. The main key on most programs is synchronization. The speaker urges viewers to try using pipes instead of forcing their system to work in a synchronized way.

- Synchronization is hard to manipulate
- Use pipes instead of forcing your system to work in a synchronized way

## [0:18:10](https://youtu.be/R3yDioKEUG8?t=1090s) Creating Pipes

The speaker explains how to create a pipe by initially creating two file descriptors and then having both the child and parent share the file descriptors of the pipe. The child removes one of them for reading, while the parent closes its first file descriptor for writing.

- Create two file descriptors
- Share file descriptors between child and parent
- Child removes one descriptor for reading
- Parent closes first descriptor for writing

## [0:19:03](https://youtu.be/R3yDioKEUG8?t=1143s) Writing and Reading from Pipes

The speaker explains that writing and reading from pipes can be done using write and read commands or by assigning a file descriptor. They provide an example where a writer and reader function are assigned, making it easier for one side to read while the other writes.

- Writing/reading from pipes can be done with write/read commands or assigned file descriptors
- Example given where writer/reader functions are assigned

## [0:20:15](https://youtu.be/R3yDioKEUG8?t=1215s) Creating Pipes Continued

The speaker continues explaining how to create pipes by showing an example where both child and parent should know what's going on with the pipe. They explain that both child and parent will have two file descriptors after the fork, and if the PID is for the child process, it will close one of them.

- Both child and parent should know what's going on with the pipe
- Both have two file descriptors after fork
- Child closes one descriptor

## [0:22:02](https://youtu.be/R3yDioKEUG8?t=1322s) Writing and Reading from Pipes Continued

The speaker explains that once a pipe is created, one side can write while the other reads. They also mention that when creating a pipe, there are normally three file descriptors in your system: standard input, standard output, and standard error. The remaining number is used for the file descriptor.

- One side writes while other reads
- Three file descriptors in system: standard input/output/error
- Remaining number used for file descriptor

## [0:23:19](https://youtu.be/R3yDioKEUG8?t=1399s) Forcing Standard Input/Output to One Side of Pipe

The speaker explains how to force standard input/output to one side of a pipe by duplicating your file descriptor using dupe. They recommend removing your original standard input before using the duplicated one.

- Duplicate file descriptor using dupe
- Remove original standard input before using duplicated one

# [0:24:43](https://youtu.be/R3yDioKEUG8?t=1483s) Using Pipes in C Programming

This video explains how to use pipes in C programming to redirect standard input or output to the corresponding input or output of a pipe. The `dup2` function is used for this purpose.

- Pipes can be used to connect two processes and allow them to communicate with each other.
- `dup2` is the preferred way of redirecting standard input or output to a pipe.
- A file descriptor is created for the pipe, and if an error occurs, it is handled by the program.

## [0:28:12](https://youtu.be/R3yDioKEUG8?t=1692s) Example Implementation

The video provides an example implementation of using pipes in C programming.

- Two child processes are created, one for executing the `ls` command and another for executing the `wc -l` command.
- The first child process sends its output to the pipe, which is then read by the second child process as its input.
- The parent process waits for both child processes to finish their execution before closing all file descriptors associated with the pipe.

# [0:34:03](https://youtu.be/R3yDioKEUG8?t=2043s) Synchronization Tools in C Programming

The video discusses synchronization tools available in C programming beyond just using pipes.

- Semaphores, mutexes, and condition variables are commonly used synchronization tools.
- While pipes can still be used for synchronization purposes, they are not as efficient as these other tools.

# [00:35:31](https://youtu.be/R3yDioKEUG8?t=2131s) Blocking Phenomena of Pipes

This section discusses the blocking property of pipes for synchronization between two processes. The reader process will be blocked until some data is pushed into the pipe. Most of the time, it's done on reading because it's not always easy to ensure that the pipe is full of data. The writer will be blocked if waiting for an empty pipe.

- Pipes can be used for synchronization between two processes.
- The reader process will be blocked until some data is pushed into the pipe.
- It's not always easy to ensure that the pipe is full of data.
- The writer will be blocked if waiting for an empty pipe.

## [00:36:24](https://youtu.be/R3yDioKEUG8?t=2184s) Synchronization using Pipes

This section explains how pipes can be used for synchronization between two processes.

- Pipes can be used to synchronize two processes.
- A child or parent can be blocked on reading or writing using pipes.
- Waiting for an empty pipe can easily be done and is often used instead of waiting for a full one.

# [00:37:09](https://youtu.be/R3yDioKEUG8?t=2229s) Example Program

This section provides an example program that uses pipes to synchronize two processes.

- An example program is given that synchronizes two processes using pipes.
- Forking is used to create child processes based on arguments passed in.
- Error checking code has been omitted from the example program.

## [00:37:21](https://youtu.be/R3yDioKEUG8?t=2241s) Child Process

This section describes what happens in the child process in the example program.

- In the child process, the read site is removed, and the parent will be doing the reading.
- The child process pretends to do something but doesn't actually do anything.
- The child process closes its file descriptor and exits.

## [00:37:52](https://youtu.be/R3yDioKEUG8?t=2272s) Closing File Descriptor

This section explains what happens when the child process closes its file descriptor.

- When the child process closes its file descriptor, no one is writing to the pipe.

## [00:37:59](https://youtu.be/R3yDioKEUG8?t=2279s) Parent Process

This section describes what happens in the parent process in the example program.

- The parent process is reading, and no one is writing anything to the pipe.
- The parent process closes its file descriptor after it reads from it.
- The parent process waits until an end-of-file argument is reached before exiting.

## [00:39:10](https://youtu.be/R3yDioKEUG8?t=2350s) Inter-process Communication using Pipes

This section discusses other ways of inter-process communication using pipes, such as P open and P close.

- Other ways of inter-process communication using pipes are done in P open and P close.
- These methods are discussed in detail in a book on this topic.

# [00:41:15](https://youtu.be/R3yDioKEUG8?t=2475s) Security Risks

This section discusses security risks associated with running programs that use pipes to open shells with higher privileges than necessary.

- Running programs that use pipes to open shells with higher privileges than necessary can pose a security risk.
- There's no guarantee that these programs will work on every system because each system might be using different versions of shell.

# [00:55:31](https://youtu.be/R3yDioKEUG8?t=3331s) Break Time

This section indicates that it's time for a break.

# [00:56:10](https://youtu.be/R3yDioKEUG8?t=3370s) Foreign

This section is unclear and doesn't provide any meaningful information.

# [0:57:27](https://youtu.be/R3yDioKEUG8?t=3447s) Creating a FIFO file

In this section, the speaker explains how to create a FIFO (First In First Out) file in Unix. A FIFO file is created using the `make fifo` command and behaves like a pipe. Other processes can access it if they know its location and have the necessary privileges.

- A FIFO file is created using the `make fifo` command.
- It behaves like a pipe, allowing other processes to access it if they have the necessary privileges.

## [0:58:18](https://youtu.be/R3yDioKEUG8?t=3498s) Reading and writing to a FIFO file

The speaker explains that reading from and writing to a FIFO file is similar to reading from and writing to any other file. However, since two different processes may be working on it simultaneously, synchronization between reading and writing is important.

- Reading from and writing to a FIFO file is similar to reading from and writing to any other file.
- Synchronization between reading and writing is important when multiple processes are accessing the same FIFO file.

## [1:00:13](https://youtu.be/R3yDioKEUG8?t=3613s) Using buffers with a FIFO file

When using buffers with a FIFO file, the size of the buffer is limited. The blocking properties of the file can be avoided by using non-blocking flags in the open function.

- When using buffers with a FIFO file, the size of the buffer is limited.
- Non-blocking flags in the open function can be used to avoid blocking properties of the file.

## [1:02:01](https://youtu.be/R3yDioKEUG8?t=3721s) Using a FIFO for inter-process communication

A child process can write data to a FIFO file, while the parent process can read from it. However, synchronization between reading and writing is important to avoid confusion.

- A child process can write data to a FIFO file, while the parent process can read from it.
- Synchronization between reading and writing is important to avoid confusion.

## [1:03:19](https://youtu.be/R3yDioKEUG8?t=3799s) Handling interruptions when writing to a FIFO file

The `O_NONBLOCK` flag in the open function can be used to handle interruptions when writing to a FIFO file. If an interruption occurs, the next statement will start from the beginning.

- The `O_NONBLOCK` flag in the open function can be used to handle interruptions when writing to a FIFO file.
- If an interruption occurs, the next statement will start from the beginning.

# [1:04:37](https://youtu.be/R3yDioKEUG8?t=3877s) Understanding FIFO in Client-Server Model

This section explains how FIFO (First In First Out) works in a client-server model. It also highlights the challenges of using FIFO in a client-server implementation.

- The first input written to the FIFO is the first output that will be read from it.
- Using FIFO in a client-server model requires generating a server FIFA known by all clients, which is used for initial communication only.
- Each client generates its own FIFA for communication with the server, and it's the client's responsibility to form this FIFA.
- Communication between clients and servers happens through specific channels unique to each client.
- Using PIDs (Process IDs) of clients is an effective way to specify specific fifos.

## [1:05:00](https://youtu.be/R3yDioKEUG8?t=3900s) Implementing Fifo

This section explains how Fifo is implemented in different architectures.

- Fifo is mostly used on a client-server model or as an HTTP server or print server.
- In peer-to-peer implementations, creating one fifo in a client-server implementation can cause problems since each client may try to write or read from that same fifo.
- There are two architectures for implementing Fifo:
  - All data sent to the server FIFA, and all corresponding writes are done through specific fifos for each client. Clients specify their messages using headers so that the server can distinguish between them.
  - Initial communication happens through one main FIFA known by everyone. Afterward, each connected pair uses its own channel for communication.

## [1:09:40](https://youtu.be/R3yDioKEUG8?t=4180s) Using Fifo for Each Client

This section discusses why using Fifo for each client may seem challenging but is necessary.

- Using a Fifo for each client may seem like it uses too many fifos, but it's the way to go.
- The same architecture applies when using sockets to share data between two processors or computers.
- To ensure that the receiving part understands what is going on, there are three ways:
  - Use fixed data of a specific size and fill the rest with garbage.
  - Use a header in front of the data to specify how many bytes will be sent.
  - Use an end-of-file character to indicate the end of data.

# [1:12:22](https://youtu.be/R3yDioKEUG8?t=4342s) Different ways to send data

This section discusses the different ways to send data and their advantages and disadvantages.

- Three ways can be used to send data, each with its own advantages and disadvantages.
- The most commonly used way has a big disadvantage logically.
- Using an idle byte is much better than just pumping data without any indication of where it starts or ends.

## [1:12:50](https://youtu.be/R3yDioKEUG8?t=4370s) Sending data in chunks

This section explains how to send data in chunks.

- You can initially say how many bytes of data you will send.
- The other process will then read that number of bytes.
- For the writer, there is a problem because they have to collect all the bytes before pushing them out. If there is a delay, they may need to fill the rest of the space with junk.
- This method causes overhead for the receiver but is still better than sending empty portions.

# [1:15:00](https://youtu.be/R3yDioKEUG8?t=4500s) FIFA Server and Client

This section talks about FIFA server and client programs.

- The program involves writing to a file and reading from a file.
- It is listed as 44-c on FIFA server and client.

# [1:15:33](https://youtu.be/R3yDioKEUG8?t=4533s) Questions

The speaker asks if anyone has any questions at this point.

# [1:20:59](https://youtu.be/R3yDioKEUG8?t=4859s) New York Passion

The speaker mentions New York Passion briefly.

# [1:28:48](https://youtu.be/R3yDioKEUG8?t=5328s) End of Video

The video ends.
