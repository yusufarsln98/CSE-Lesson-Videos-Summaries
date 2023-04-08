# CSE 344 | 4th Week | 21.03.2023-L1

## [0:00:02](https://youtu.be/Nct80B\_Mv0k?t=2s) Introduction

Overview: The instructor introduces the topic of signals and processes in Unix-like operating systems.

* Signals and processes are important concepts in Unix-like operating systems.
* The instructor makes a joke that some female students found inappropriate.
* The lecture will cover the fundamentals of signals and how to handle them, as well as creating processes in Unix-like operating systems.

## [0:01:25](https://youtu.be/Nct80B\_Mv0k?t=85s) Signals

Overview: The lecture covers the basics of signals, including their purpose and how to handle them.

* Signals were initially used to end a process but have since been modernized to act like software interrupts.
* When a signal is generated, execution stops and the necessary function is performed.
* Signals can happen at any time during execution, so handling them requires caution.
* There are three ways to handle a signal: ignore it, take the default action (usually terminate), or execute a custom signal handler.
* A signal handler is limited in what it can do, and certain C library calls cannot be used while handling signals.
* There are many predefined signals in signal.h, with most having default actions of ignore or termination. Two user-defined signals also exist.

## [0:07:22](https://youtu.be/Nct80B\_Mv0k?t=442s) Handling Signals

Overview: This section discusses how to handle signals in a program.

* If a process doesn't have the privilege to send a signal, you'll receive -1 with an error number.
* If there are no processes like that, you'll receive a special error saying "no such process."
* Some processes cannot be killed by normal users, and some exceptions allow for blocked functions to continue.
* You can handle signals by ignoring them, blocking them, or writing a signal handler function.

### [0:09:18](https://youtu.be/Nct80B\_Mv0k?t=558s) Unkillable Processes

Overview: This section discusses processes that should not be killed.

* Some processes generated by the root of the system should not be killed by normal users.
* Exceptions allow for blocked functions to continue if they are suspended until unblocked.
* Two signals cannot be blocked - SIGSTOP and SIGKILL.

### [0:10:09](https://youtu.be/Nct80B\_Mv0k?t=609s) Sending Signals

Overview: This section discusses how to send signals in a program.

* You can send yourself a signal or raise one and receive it through the signal handler function.
* The way to handle signals is using `sigprocmask` which allows you to block, unblock or mask them.
* Define a set of signals and add the ones you want to manipulate into that set.

### [0:11:56](https://youtu.be/Nct80B\_Mv0k?t=716s) Signal Sets

Overview: This section discusses how to work with signal sets in a program.

* Define a signal set and add the signal(s) you want to deal with into that set.
* You can fill the set with another set and check if a signal is in that set using `Sigismember` function.
* You can block, unblock or mask signals using `sigprocmask`.
* Two signals cannot be blocked - SIGSTOP and SIGKILL.

### [0:13:37](https://youtu.be/Nct80B\_Mv0k?t=817s) Blocking and Unblocking Signals

Overview: This section discusses how to block and unblock signals in a program.

* Define a mask to block or unblock signals.
* Use `sigprocmask` to apply the mask.

## [0:14:38](https://youtu.be/Nct80B\_Mv0k?t=878s) Asynchronous Programming and Signal Handling

Overview: In this section, we learn about asynchronous programming and signal handling in Unix.

* If a signal happens before you set a plug to that second somewhere in execution, the portion of the code will not be executed.
* Be careful when working with asynchronous programming as signals can happen at any time.
* You can check if a signal is pending or not using `sigpending()`.
* To take action when receiving a signal, you need to write a signal handler. The action is defined in a structure called `sigaction`.
* The `sigaction` structure defines the function that will be executed and the flags that are set.
* When executing the signal handler function, it's important to limit what you do inside it. It should be atomic and not try to create a world or run big programs.
* You can ignore signals by assigning them to the default action or using `SIG_IGN`.
* From the perspective of the operating system, there are two executions going on when a signal happens - the main program execution and the signal handler execution.
* If you change global variables inside the signal handler, it will affect the main program execution when it resumes.

### [0:15:26](https://youtu.be/Nct80B\_Mv0k?t=926s) Ignoring Signals

* You can ignore signals by assigning them to their default action or using `SIG_IGN`.
* Use `sigpending()` to check if a signal is pending or not.

### [0:16:23](https://youtu.be/Nct80B\_Mv0k?t=983s) Writing Signal Handlers

Overview: In this section, we learn how to write signal handlers.

* To take action when receiving a signal, you need to write a signal handler.
* The action is defined in a structure called `sigaction`.
* The `sigaction` structure defines the function that will be executed and the flags that are set.
* When executing the signal handler function, it's important to limit what you do inside it. It should be atomic and not try to create a world or run big programs.

### [0:20:07](https://youtu.be/Nct80B\_Mv0k?t=1207s) Asynchronous Programming and Signal Handling

Overview: In this section, we learn about how asynchronous programming and signal handling affect program execution.

* From the perspective of the operating system, there are two executions going on when a signal happens - the main program execution and the signal handler execution.
* If you change global variables inside the signal handler, it will affect the main program execution when it resumes.
* The output of program execution may differ each time if you do something funky with the signal handler.

## [0:22:09](https://youtu.be/Nct80B\_Mv0k?t=1329s) Handling Signals in C

Overview: This section discusses the importance of handling signals carefully in C, as most C functions are not compatible with signal handling. It also covers ways to wait for a signal without busy waiting and how to handle errors that may occur during signal handling.

* Variables on the main execution can change due to what is done in the signal handler, so it's important to be careful.
* If you want to execute something right after a signal handler, you have to restart what was going on before the raise of that signal happened.
* Most C functions in the C library are not compatible with signal handling.
* Waiting for a signal can be done using sleep, nanosleep or suspend.
* Busy waiting should be avoided as it takes up CPU cycles. Instead, use sleep or pause to tell the operating system that you're doing nothing at this instant.
* Setting a flag for an action when we don't know when the signal will happen can lead to buggy code. Using suspend can help block signals until execution is finished.
* Errors that occur during signal handling may cause error numbers to change. It's good practice to store error numbers somewhere and put them back after execution of the signal handler ends.

### [0:28:38](https://youtu.be/Nct80B\_Mv0k?t=1718s) Conclusion

No new content provided.

## [00:29:15](https://youtu.be/Nct80B\_Mv0k?t=1755s) Writing Signal Handlers

Overview: When writing a signal handler, only include necessary code and avoid using C library calls as they are not synchronously safe. Be careful when using multi-process or multi-threaded operations as the signal handler may access global variables associated with the main execution.

* The program will behave differently when a signal happens compared to when no signal happens.
* Avoid reinventing everything in the signal handler and keep it simple.
* Use minimal code, such as writing to a log file and terminating if needed.
* C library calls are not synchronously safe, so be cautious when using them in multi-process or multi-threaded operations.
* The same signal handler may access global variables associated with the main execution, which can lead to unpredictable results.

### [00:31:54](https://youtu.be/Nct80B\_Mv0k?t=1914s) Creating Another Process Inside a Process

Overview: A new process is created by executing a program after it has been written. The operating system creates the process and allocates resources for it. There are five states that one process can be in.

* A new process is created by executing a program after it has been written.
* The operating system creates the process and allocates resources for it.
* There are five states that one process can be in: ready state, running state, blocked state, terminated state, and dead state.
* If a process gets blocked during execution due to an I/O operation or software interrupt, it will be put into the block state until completion before returning to the ready state.
* Two ways of creating another process inside an existing one are calling a function from a terminal or creating an exact copy of the current program/process.

## [0:36:37](https://youtu.be/Nct80B\_Mv0k?t=2197s) Terminal and Command Usage

Overview: This section discusses the use of terminals and commands in Unix systems.

* Terminals can generate another process, which can handle other programs.
* There are different types of terminals in Unix systems, making it difficult to know which one your program is running on.
* Using a terminal to run a command comes with security risks.

### [0:49:24](https://youtu.be/Nct80B\_Mv0k?t=2964s) System Command

Overview: This section discusses the system command in Unix systems.

* The system command generates a terminal and calls another process from that terminal.
* The LS L command is used as an example.
* Errors that occur within the called command are handled by the terminal.

### [0:51:23](https://youtu.be/Nct80B\_Mv0k?t=3105s) Creating Processes

Overview: This section discusses creating processes in Unix systems.

* Windows API has a family of functions for creating new processes inside one.
* In Unix, there are two ways to create a process inside another process - fork/exec or just fork.
* Fork/exec executes a system call through a family of functions without creating another terminal or shell.

## [0:53:12](https://youtu.be/Nct80B\_Mv0k?t=3192s) Understanding Fork

Overview: This section discusses the concept of forking in multi-processing and how it creates an exact copy of a process.

* A fork is called an exact copy of the process.
* The child does whatever is required while the parent only waits for it.
* Hanging an execution to another and just waiting for it is not a good way of using system resources.

### [0:54:44](https://youtu.be/Nct80B\_Mv0k?t=3284s) Using Fork without Weighting

Overview: This section explains how to use Fork without weighting and why it's important to be careful when executing code in both processes.

* You should assign some other stuff to the main execution instead of just busy waiting for that.
* The execution of this child and the execution in the main process might affect each other.
* You have to give each execution a proper route by looking at their process IDs or be very careful about what you're doing.

### [0:56:00](https://youtu.be/Nct80B\_Mv0k?t=3360s) Manipulating Processes with PID

Overview: This section explains how to manipulate processes using PID and separate parent and child executions.

* Every variable you change in here, you manipulate on both parents and child processes.
* If `child_pid` is not zero, that means that this is where the parent is working on. Else, that means the `child_pid` is zero, which indicates where the child is working on.
* Parent executes one portion while the child executes another portion.

### [0:59:18](https://youtu.be/Nct80B\_Mv0k?t=3558s) Understanding Child as Exact Copy

Overview: This section discusses how a child is an exact copy of the parent and how file descriptors are accessible by both processes.

* The child is now an exact copy of the parent, and all data heap and stack everything is the same.
* All those file descriptors that are present before the execution of the fork are now also accessible by the child.
* Any read, write, or seek operation done either by the child or parent will affect both of them.

## [1:01:09](https://youtu.be/Nct80B\_Mv0k?t=3669s) Number of Processes

Overview: In this section, the speaker discusses how many processes are created at different points in the code.

* At the first fork, there are two processes.
* At the second fork, there are three processes.
* After executing a certain portion of code, eight processes have been formed.

### [1:03:08](https://youtu.be/Nct80B\_Mv0k?t=3788s) Executions and Forks

* After the second fork, there are six executions.
* If any process has C2 greater than zero, it will execute another fork.
* The last fork will be executed by one of the eight processes created earlier.

### [1:06:13](https://youtu.be/Nct80B\_Mv0k?t=3973s) Using Fork

Overview: The speaker talks about using Fork to create new processes and how it can be both powerful and problematic.

* When using Fork to create new processes, you must be careful because you don't know which process will execute which portion of code.
* Each process is waiting for an execution turn decided by the kernel of the operating system.
* It may be easier to use other methods such as forking out or executing a command and waiting for the child to finish rather than dealing with all these complexities.

## [1:09:46](https://youtu.be/Nct80B\_Mv0k?t=4186s) Handling Exits and Error Codes

Overview: In this section, the speaker talks about handling exits and error codes in shell scripts.

* Be careful with requests for init to get rid of resources as they may be done instantaneously on some exits.
* Keep track of the code by using a special character.
* The result of echo may differ depending on the shell being used.
* Use "echo $?" to display the latest error code on that shell.
* Error codes may differ depending on the shell being used.

### [1:11:09](https://youtu.be/Nct80B\_Mv0k?t=4269s) Handling Errors at Exit

* To see the error code after termination of a process, use "echo $?" command.
* Use this command to get rid of log files or dump memory before exiting abnormally.

### [1:12:03](https://youtu.be/Nct80B\_Mv0k?t=4323s) Unstoppable Signals

* Some signals like SIGKILL cannot be blocked or handled and will just kill the process.
* Examples of signal creation and handling were shown earlier in the lecture.

### [1:12:54](https://youtu.be/Nct80B\_Mv0k?t=4374s) End of Lecture

Overview: The speaker announces that there will be no lecture on Thursday due to Ramadan but will return to normal schedule afterwards. No further content is provided.

No new line needed after last bullet point.