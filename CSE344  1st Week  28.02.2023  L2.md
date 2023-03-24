# CSE344 | 1st Week | 28.02.2023-L2

## [0:00:02](https://youtu.be/FePITzVOgEs?t=2s) Introduction

Overview: The video introduces the concept of a shell, which is a special purpose program designed to read commands typed by the user and execute appropriate programs.

* A terminal emulator is a type of shell used in Unix systems and Windows.
* There are many types of shells that can work on the same computer simultaneously.
* Shells help users understand what their programs are doing and display information through standard input, output, and error.

## [0:01:17](https://youtu.be/FePITzVOgEs?t=77s) Users and Groups

Overview: The video explains how computers are designed for multiple users or groups to execute programs together. Users have unique IDs and passwords, while groups allow file sharing between users.

* Administrative group controls other users.
* File structure includes directories (rounded edges) and files (rectangular shapes).
* Symbolic links include dot (link to directory itself) and two dots (link to parent directory).
* Hardlinks and softlinks will be covered later in the course.
* Dangling links occur when a file or directory has been deleted but still exists in the system's database.
* File paths can be relative to root (-) or current working directory.

## [0:02:59](https://youtu.be/FePITzVOgEs?t=179s) Symbolic Links

Overview: This section covers symbolic links in more detail.

* Symbolic links are not directories but link to directories above themselves.
* Dot symbol link refers directly to itself, while two dots refer to parent directory.
* Hardlinks and softlinks will be covered later in the course.

## [0:05:14](https://youtu.be/FePITzVOgEs?t=314s) Relative Linking

Overview: This section explains how file paths can be relative to the root or current working directory.

* File paths starting with a dash are relative to the root.
* File paths without a dash are relative to the current working directory.
* Part name refers to the file or directory's name in the file system.

## [0:06:53](https://youtu.be/FePITzVOgEs?t=413s) Absolute Path Names and Current Working Directory

Overview: This section explains the concept of absolute path names and current working directory.

* An absolute path name begins with a slash.
* The current working directory starts from the home directory when you log into your computer.
* In this example, there are two users, AVR and MTK. When AVR logs in, it will start in one directory, while MTK will start in another.
* The administrator or root user has access to all directories, while other users may not have access to certain directories.

### [0:08:19](https://youtu.be/FePITzVOgEs?t=499s) File Input/Output (I/O)

Overview: This section discusses how to communicate with the kernel for opening, reading, writing files using system calls.

* Most applications use library interprets ASCII code 10 decimal as a new line and end of file is a special character called Endo file.
* There are system calls that support commands for opening, reading, writing files.
* When you open a file using `open`, you end up with three descriptors - standard input (input from keyboard), standard output (output to screen), and standard error (where errors are printed).
* Standard input and standard output are buffered while standard error is written directly because errors are important.

### [0:12:16](https://youtu.be/FePITzVOgEs?t=736s) Compiling Programs

Overview: This section explains how programs are compiled into machine-readable binary code.

* Programs written in C consist of source code and machine-readable binary code.
* When executing a program, the operating system loads the binary part into virtual memory created by the operating system.
* The instructions that need to be executed are taken to the CPU and executed, changing corresponding terms on the RAM until the next instruction comes in.

## [0:14:41](https://youtu.be/FePITzVOgEs?t=881s) Introduction to Processes

Overview: This section provides an introduction to processes and how they work in a computer system.

* A process is created by compiling source code into binary that the machine can understand.
* The binary is loaded into the system and allocated necessary databases by the operating system.
* The process has segments called text, data, and stack.
* The text segment contains instructions from the program's source code.
* The data segment stores static variables.
* The stack grows and shrinks as the program executes, storing local variables with known sizes.

### [0:17:14](https://youtu.be/FePITzVOgEs?t=1034s) Forking a Process

Overview: This section explains how a process can create an exact replica of itself using fork.

* Fork creates an exact replica of the calling process with a different ID.
* The child process has the same size of entries for text, data, heap, and stack as the parent process.
* Normal executions involve changing data in these segments without changing code.
* When execution finishes, all resources are freed so they can be replaced by new executions.

### [0:19:42](https://youtu.be/FePITzVOgEs?t=1182s) Main Execution and PID

Overview: This section discusses main execution and PID (process identification).

* Every process has at least one execution called main execution or main thread.
* Each process has a unique ID called PID for identification purposes.
* When a parent process creates another using fork, it will also have its own PID but will need to use ppid (parent's process ID) to access its parent's ID.

### [0:21:10](https://youtu.be/FePITzVOgEs?t=1270s) Determination Requests and Exit System Call

Overview: This section explains how determination requests are made and how the exit system call is used.

* Determination requests of a process are done using the exit system call.
* The kernel prepares the necessary kill signal to ensure proper execution and returns with necessary return variables.
* The parent waits for the child to finish executing.

## [0:22:05](https://youtu.be/FePITzVOgEs?t=1325s) Descriptive Title

Overview: The speaker discusses the use of demons and human processes in operating systems, and how they are designed to run for a long time. They also explain the importance of synchronizing processes when using Fork.

* Demons are special processes that run in the background and are designed to perform specific operations.
* Human processes, such as print servers or HTTP servers, are also designed to run for a long time.
* Demons do not write to standard output but may write to log files or other files.
* Every execution has an environmental list with variables maintained in user space.
* When a new process is created via Fork, it has the same environmental list as its parent.
* Synchronizing processes is important because you don't know which execution will be held by the kernel at which time.

### [0:26:24](https://youtu.be/FePITzVOgEs?t=1584s) Memory Mapping

Overview: The speaker explains memory mapping and how it can be used to allocate memory for a process.

* Memory mapping is mostly done by mm map system calls, which generate a new memory mapping for the process's virtual address space on the Heap most of the time.
* Private memory is used only by the process itself while shared memory can be shared with other processes.
* Using shared memory is a fast way of sharing data between processes, especially between child and parent processes.

## [0:29:05](https://youtu.be/FePITzVOgEs?t=1745s) Static vs Shared Libraries

Overview: The speaker discusses the differences between static and shared libraries, including their advantages and disadvantages.

* Static libraries are combined directly into a program when compiled, making it larger but easier to run on different systems.
* Changing functions in a static library will not affect previously compiled programs, which can be problematic if errors are found later.
* Shared libraries are included at runtime and take up less space on the hard disk, but may cause unexpected behavior due to differences in libraries across systems.

### [0:32:23](https://youtu.be/FePITzVOgEs?t=1943s) Interprocess Communication and Synchronization

Overview: The speaker discusses the importance of synchronization when using multiple processes at once and introduces various techniques for interprocess communication.

* When using multiple processes, synchronization is necessary to ensure proper execution order.
* Interprocess communication (IPC) techniques include signals, pipes/fifos, sockets, file locking, message queues, semaphores/mutexes, and shared memory.
* Signals are used to notify other processes of errors or terminate them. Pipes/fifos process data between processes. Sockets share data between different computers. File locking prevents access to locked portions of a file. Message queues send data between two processes. Semaphores/mutexes synchronize access to shared resources. Shared memory allows variables to be shared between processes on the same memory page.

## [0:35:48](https://youtu.be/FePITzVOgEs?t=2148s) Signals and Signal Handlers

Overview: In this section, we learn about signals and signal handlers in operating systems.

* Signals are important as they allow for software interrupts.
* When a signal arrives, you can ignore it, do what the signal wants (usually killing or terminating), or suspend it until a specific portion of code is finished.
* You can use a signal handler to select what to do with a signal. This is just a function in the code that is executed when you receive a signal.
* When a signal arrives, multiple executions may be working at the same time.
* You may receive multiple signals, including the same signal more than once.

### [0:38:18](https://youtu.be/FePITzVOgEs?t=2298s) Handling Multiple Signals

* If you ignore a signal, it cannot be recalled anymore. If you suspend it, it will act like a pending process.
* There are ways of handling signals so that all three operations (ignore, do what the signal wants, suspend) can be done on them.
* We will work on how to handle these kinds of things during the course of this lecture.

### [0:39:04](https://youtu.be/FePITzVOgEs?t=2344s) Threads vs Fork

Overview: In this section, we learn about threads and fork in operating systems.

* Using fork creates another execution of ourselves with the main thread inside but uses many system resources.
* Creating another execution with threads is called lightweighting. It does not require generating all these resources in memory or disk space like fork does.

### [0:40:26](https://youtu.be/FePITzVOgEs?t=2426s) Lightweight Execution

Overview: In this section, we learn about lightweight execution in operating systems.

* Threads are a lightweight form of execution that can do limited things from the Kernel's perspective.
* The Kernel only sees the whole thing as a whole theoretically.

### [0:41:22](https://youtu.be/FePITzVOgEs?t=2482s) Questions and Answers

Overview: In this section, questions are asked and answered about the previous topics.

* A question is asked about why the operating system stops other processes instead of lowering their resources. The answer is not clear from the transcript.
* Other questions are asked but are not clear from the transcript.

## [0:43:57](https://youtu.be/FePITzVOgEs?t=2637s) Processes vs Threads

Overview: The operating system can select and execute multiple processes, but when it comes to threads, the OS only knows that one process is running. Synchronization is needed between thread executions using condition variables, mutexes or semaphores.

* Global variables of a process are available for all its threads.
* Multiple threaded implementations use less resources than multi-process implementations.
* Communication between threads can be done through memory allocation or sockets.
* Multi-process implementations allocate more space and have specific memory for each process.

### [0:48:18](https://youtu.be/FePITzVOgEs?t=2898s) Time and Date

Overview: There are two types of time - real time and CPU time. Real time refers to the standard calendar used worldwide while CPU time starts from the first time you turn on your computer.

* Real time is used to synchronize between multiple computers.
* CPU time is used for processes working on the same computer.
* Client-server architecture involves a client requesting something from a server which returns the corresponding result.
* Server sends requests to access hardware while clients use the results returned by servers.

### [0:50:18](https://youtu.be/FePITzVOgEs?t=3018s) Real-time Applications

Overview: Real-time applications require timely responses to inputs within strict deadlines.

No further content provided in this section.

## [0:51:13](https://youtu.be/FePITzVOgEs?t=3073s) Real-Time Applications

Overview: In this section, the speaker discusses real-time applications and their importance in certain industries.

* Operating systems decide which process will be on the CPU and when it will be executed.
* Some applications need to be executed at specific time intervals, such as navigation systems or nuclear plants.
* Braking systems in cars also use time and need to be controlled periodically.
* Real-time applications should be guaranteed by a certain deadline time.
* Linux is not a real-time operating system, so extra scheduling algorithms are needed to ensure real-time operations.

### [0:53:01](https://youtu.be/FePITzVOgEs?t=3181s) Hard vs Soft Real-Time Systems

* Hard real-time systems guarantee that an operation will be done within a certain deadline time.
* Soft real-time systems still prioritize the operation but may not guarantee it if it falls below a certain number of times.
* The scheduling algorithm and kernel determine whether an operating system can establish hard or soft real-time systems.

## [0:57:06](https://youtu.be/FePITzVOgEs?t=3426s) Summary

Overview: The speaker summarizes the topics covered in this lecture about system programming and operating systems.

* Real-time applications are important in various industries and require specific timing intervals for execution.
* Linux is not a real-time operating system, so extra scheduling algorithms are needed for real-time operations.
* Hard vs soft real-time systems depend on the number of times an operation can be guaranteed within a deadline time.
