# [00:00:02](https://youtu.be/Vdo7wd0_obM?t=2s) Introduction

The speaker introduces the topic of the lecture and mentions that they will be building on what was covered in a previous lecture.

- The lecture will focus on processes.
- When creating a child process, it is important to know what is happening with the child.
- Two commands can be used to determine this: wait and catch a signal called "sick child".

# [00:01:03](https://youtu.be/Vdo7wd0_obM?t=63s) Wait Command

The speaker explains how to use the wait command to determine what has happened with a child process.

- The parent process waits for the child process to return.
- The PID of the terminated child is returned by wait().
- If multiple children are created, it may not be clear which one has terminated.

# [00:02:10](https://youtu.be/Vdo7wd0_obM?t=130s) Limitations of Wait Command

The speaker discusses some limitations of using the wait command.

- It is a blocking process, meaning that it waits until a child returns or a signal returns before continuing.
- It may not be clear which child has terminated if multiple children are created.
- A simple program daemonstrates how to use wait().

# [00:03:53](https://youtu.be/Vdo7wd0_obM?t=233s) Code Example

The speaker provides an example code that daemonstrates how to use fork() and wait() functions in C programming language.

- The code creates multiple processes using fork().
- Each process sleeps for some time before terminating.
- The parent process waits for all children processes using wait().

# [00:09:25](https://youtu.be/Vdo7wd0_obM?t=565s) System Calls

The speaker briefly discusses system calls.

- System calls are used to request services from the operating system.
- They provide an interface between a process and the operating system.
- Examples of system calls include fork(), wait(), and exec().

# [00:10:09](https://youtu.be/Vdo7wd0_obM?t=609s) Conclusion

The speaker concludes the lecture by thanking the audience for their attention.

- The lecture covered processes and how to determine what is happening with child processes.
- Wait() command can be used to determine what has happened with a child process, but it has some limitations.
- A simple program daemonstrated how to use wait().
- System calls provide an interface between a process and the operating system.

# [0:14:11](https://youtu.be/Vdo7wd0_obM?t=851s) After the Fork

In this section, the speaker discusses what happens after a fork in the code. The child process will execute and print out its PID before sleeping for a certain amount of time.

- After a fork, the child process will execute.
- The child process will print out its PID.
- The child process will sleep for a certain amount of time.

# [0:14:37](https://youtu.be/Vdo7wd0_obM?t=877s) Child Process Execution

The speaker explains how the parent process can continue executing while waiting for the child processes to finish. They also discuss how to use sleep and loops to control execution.

- Parent process can continue executing while waiting for child processes to finish.
- Sleep can be used to control execution timing.
- Loops can be used to ensure all child processes are executed.

# [0:15:00](https://youtu.be/Vdo7wd0_obM?t=900s) Printing Child PIDs

The speaker explains how to print out the PIDs of each child process as they complete their execution using wait() and status.

- Wait() can be used to wait for a specific child process.
- Status returns information about which child has completed execution.
- PIDs of each completed child can be printed out using status.

# [0:16:15](https://youtu.be/Vdo7wd0_obM?t=975s) Waiting for Specific Child Processes

The speaker discusses how to wait for specific child processes by using their PIDs instead of just waiting for any one of them with wait().

- Wait() waits for any one of multiple children processes.
- Using PID with options allows you to wait specifically for one particular child process.
- Usage is similar to wait(), but with different options.

# [0:17:11](https://youtu.be/Vdo7wd0_obM?t=1031s) Wait() vs. PID with Options

The speaker compares the usage of wait() and PID with options, explaining when to use each one.

- Wait() waits for any child process to complete.
- PID with options allows you to wait specifically for one particular child process.
- Usage is similar, but PID with options is more specific.

# [0:18:26](https://youtu.be/Vdo7wd0_obM?t=1106s) Printing Child Status

The speaker explains how to print out the status of a child process using waitpid() and WIFEXITED.

- Waitpid() can be used to wait for a specific child process.
- WIFEXITED returns information about how the child exited.
- Printing out the status can help understand why a child has left execution.

# [0:19:18](https://youtu.be/Vdo7wd0_obM?t=1158s) Writing Signal Handlers

The speaker discusses writing signal handlers for child processes in order to handle signals raised by their termination.

- Writing signal handlers allows you to handle signals raised by terminated children.
- It is good practice to have each child handle its own signals.
- This helps ensure that the parent knows which child has terminated and why.

# [00:21:38](https://youtu.be/Vdo7wd0_obM?t=1298s) Child Processes and Signal Handling

This section discusses the cleanup process when a child process is terminated, and how to notify the parent process of the termination. It also covers two modes of creating child processes, orphan processes, and zombie processes.

- When a child process is terminated, it's important to clean up any resources it was using and notify the parent process. This can be done by writing to a log or de-establishing the handler.
- Orphan processes are created when a parent process creates multiple children but terminates before they do. The kernel will take ownership of these orphaned children and wait for them to finish executing.
- Zombie processes occur when a child dies but its status is still kept in the kernel's database. If weight statements are not performed by either the main or init process, these zombie processes can accumulate and fill up the kernel's process table, preventing new processes from being created.

# [00:22:29](https://youtu.be/Vdo7wd0_obM?t=1349s) Date ID

This section briefly covers date ID as an option for identifying child processes.

- Date ID is similar to PID and wait statements but provides additional options that may not be relevant in some cases.

# [00:23:27](https://youtu.be/Vdo7wd0_obM?t=1407s) Orphan Processes

This section goes into more detail about orphan processes.

- Orphaned children are owned by the kernel until they finish executing.
- The resources allocated for orphaned children will stay in memory until they're released through weight statements.
- Failure to perform weight statements can lead to accumulation of zombie processes that fill up the kernel's process table.

# [00:24:26](https://youtu.be/Vdo7wd0_obM?t=1466s) Zombie Processes

This section covers zombie processes in more detail.

- Zombie processes occur when a child dies but its status is still kept in the kernel's database.
- The kernel will keep some portions of the allocated space for the child so that the parent can go and ask what happened to the child.
- Failure to perform weight statements can lead to accumulation of zombie processes that fill up the kernel's process table.

# [00:25:48](https://youtu.be/Vdo7wd0_obM?t=1548s) Eliminating Zombie Children

This section discusses how to eliminate zombie children.

- It's important to perform weight statements after a child process terminates so that its resources are released and it doesn't become a zombie process.
- Accumulation of zombie processes can fill up the kernel's process table, preventing new processes from being created.

# [00:27:22](https://youtu.be/Vdo7wd0_obM?t=1642s) Summary

This section provides a summary of the previous sections on child processes, orphaned children, and zombie processes.

# [00:29:51](https://youtu.be/Vdo7wd0_obM?t=1791s) Drama, Videos, and Television

This section discusses different types of media.

- Drama
- Videos
- Television

# [00:30:24](https://youtu.be/Vdo7wd0_obM?t=1824s) Child Processes

This section discusses child processes.

- Refers to a child process mentioned earlier
- Ramen is mentioned but it's unclear why
- Navigable order for foreign processes in Minnesota

# [00:32:21](https://youtu.be/Vdo7wd0_obM?t=1941s) Good Programming Practice

This section discusses good programming practices.

- Minnesota had all the students' processes
- Good programming practice requires using system calls
- Discourages calling during lectures as it uses extra resources
- Example uses system call after forking child process with episode 0
- Exiting does not completely release all resources; zombies may still exist
- Parent waits a little bit before using PS grab to get PID of child just created
- Killing zombie may not be enough to get rid of zombie process

# [00:35:12](https://youtu.be/Vdo7wd0_obM?t=2112s) Handling Child Processes

This section discusses handling child processes.

- Writing a handle for signal sick child can help control child processes better
- Creating a new process can be done by generating a clone of yourself using Fork then using exact family calls
  - This generates an exact replica of yourself and uses exec in the library
  - The way it works is you fork your system and generate an exact replica of yourself then use exec

# [0:39:17](https://youtu.be/Vdo7wd0_obM?t=2357s) Understanding the Exact Family of Functions

In this section, the speaker explains how the exact family of functions works and what happens when they are called.

- The exact family of functions replaces the content of a memory location with whatever function or program is called in it.
- After calling exec on the main process, all processes inside are emptied and replaced with whatever function is being called.
- The execution of this new process is independent of the parent process, but signals generated inside will affect it if not handled properly.
- Using someone else's program with exec can have pros and cons. If you know what to expect from a system function like grep or less, you can leave it be. But if it's someone else's program, beware that side effects happening on the child will also affect the parent process.

## [0:40:47](https://youtu.be/Vdo7wd0_obM?t=2447s) Possible Errors When Using Exec

The speaker discusses some possible errors that may occur when using exec.

- The total space required for a program may be more than what's allowed by your system.
- You may not have permission to execute a script file because it hasn't been given executable privileges.
- There may be no file in that path or another process is currently using it.

## [0:43:21](https://youtu.be/Vdo7wd0_obM?t=2601s) Best Practices for Using Exec

The speaker shares best practices for using exec.

- Instead of writing a whole new program, use an existing one directly instead.
- If you must use exec, fork yourself first and call the function inside the child to avoid affecting the main process.
- Beware that if you don't know how a program behaves when called with exec, side effects happening on the child will also affect the parent process.

# [0:46:22](https://youtu.be/Vdo7wd0_obM?t=2782s) Introduction to Shell Implementation

In this section, the instructor introduces the concept of shell implementation and explains that it is not feasible for students to implement all system calls by themselves. Instead, they can use a system call via fork, exec, wait, and exit to make their implementation more efficient.

- Shell implementation requires many system calls
- It is not feasible for students to implement all system calls by themselves
- Using a system call via fork, exec, wait, and exit makes the implementation more efficient

# [0:47:37](https://youtu.be/Vdo7wd0_obM?t=2857s) Functions in Shell Implementation

The instructor briefly mentions functions in shell implementation.

- Functions are important in shell implementation

# [0:48:20](https://youtu.be/Vdo7wd0_obM?t=2900s) Simple Shell Implementation Example

The instructor provides an example of a simple shell implementation using fork, exec, wait and exit commands.

- Get command from user input
- Use system command with the obtained command
- Return status of the executed command to original process using process ID
- Print status of child process execution

# [0:51:18](https://youtu.be/Vdo7wd0_obM?t=3078s) Advantages of System Calls

The instructor explains that while using a system call may be inefficient from a programming perspective, it can be more efficient from a systems perspective. He also emphasizes the importance of writing optimum code.

- Implementing and executing a system command using fork, exec, wait and exit commands may be complicated on the programmer side but can be more efficient on the kernel side.
- Writing optimum code is important even if systems are powerful nowadays.

# [0:54:06](https://youtu.be/Vdo7wd0_obM?t=3246s) Using System Calls to Track Errors

The instructor explains that using system calls can be a good way to track errors in a system.

- Using system calls can be a good way to track errors in a system
- The program presented uses the system call insider program to write what is going on with it.

# [0:56:07](https://youtu.be/Vdo7wd0_obM?t=3367s) Security Risks of Changing User and Group ID

In this section, the speaker warns against calling a program inside another program with changed user and group IDs as it can cause security breaches. Although most systems are now aware of this issue, it is still important to avoid using this method.

- Calling a program inside another program with changed user and group IDs can cause security breaches.
- Most systems are now aware of this issue and avoid using this method.

# [0:56:32](https://youtu.be/Vdo7wd0_obM?t=3392s) Implementing Fork, Exec, Wait, and Exit

The speaker suggests implementing the same system using Fork, Exec, Wait, and Exit instead of executing a shell command or generating a terminal inside a program using XCL. This can be done by generating an exact duplicate of the process being worked on using Fork before executing the system command from the child.

- Implementing Fork, Exec, Wait, and Exit is suggested instead of executing a shell command or generating a terminal inside a program using XCL.
- Generating an exact duplicate of the process being worked on using Fork before executing the system command from the child is necessary.

# [0:57:16](https://youtu.be/Vdo7wd0_obM?t=3436s) Using Exact Command to Execute Sh from Child

The speaker explains how to use exact command to execute sh from the child. Before forking, there are two processes - parent and child. After execution of exact CL in child process whatever HS has will be dumped into that location.

- Before forking there are two processes - parent and child.
- After execution of exact CL in child process whatever HS has will be dumped into that location.

# [0:58:23](https://youtu.be/Vdo7wd0_obM?t=3503s) Benefits and Downsides of Using Fork, Exec, Wait, and Exit

The speaker discusses the benefits and downsides of using Fork, Exec, Wait, and Exit. The benefit is that an external program or another shell/terminal does not need to be created. However, the downside is that the parent process needs to wait for the child process and take care of any errors or signals that occur during execution.

- Benefit: An external program or another shell/terminal does not need to be created.
- Downside: The parent process needs to wait for the child process and take care of any errors or signals that occur during execution.

# [0:59:13](https://youtu.be/Vdo7wd0_obM?t=3553s) Writing a Handler for Child Sick Signal

The speaker explains how to write a handler for child sick signal when trying to mimic system call in a way or limit mimic something like this. It is important to make sure that whatever is happening inside the child is still appropriately going on.

- Write a handler for child sick signal when trying to mimic system call in a way or limit mimic something like this.
- Make sure that whatever is happening inside the child is still appropriately going on.

# [1:00:03](https://youtu.be/Vdo7wd0_obM?t=3603s) Ignoring Signals Before Executing from Child

The speaker emphasizes ignoring signals before executing from child as these signals might cause the parent to terminate which will orphan whatever you're executing at their views on the child. It's good programming practice just to quit signals before executing those things.

- Ignore signals before executing from child.
- Good programming practice just to quit signals before executing those things.

# [1:01:18](https://youtu.be/Vdo7wd0_obM?t=3678s) Importance of Ignoring Kill and Ctrl C on Daemons

The speaker explains the importance of ignoring kill and Ctrl C on daemons as the daemon has to run for a very long time without being interrupted.

- It's important to ignore kill and Ctrl C on daemons.
- The daemon has to run for a very long time without being interrupted.

## [1:18:49](https://youtu.be/Vdo7wd0_obM?t=4729s) Implementing a System Call using Fork, Exec and Wait with Proper Signal Handling

In this section, the speaker explains how to implement a system call using fork, exec and wait with proper signal handling. The steps are:

- Block all child-related signals
- Ignore end and quit signals
- Use the function `fork()`
- Put all signals back into their original state
- Leave properly

## [1:22:15](https://youtu.be/Vdo7wd0_obM?t=4935s) Raising Daemons

In this section, the speaker talks about raising daemons. Daemons are programs that are created at startup of the system boot and run until they are down. They are used for printer handling, hardware handling, login screens etc. The key points are:

- Daemons should not be related to terminal job control things or some signals like sick or six stop sync up.
- Killing a daemon is like saying you will not use that hardware from this portion on.
- When creating a daemon, be aware that it should be free from the terminal job control things and some signals.

# [1:24:45](https://youtu.be/Vdo7wd0_obM?t=5085s) Creating a Daemon

In this section, the speaker discusses how to create a daemon in programming.

- The fundamental way of creating a daemon is by performing a fork.
- The child process should manipulate its inputs and outputs accordingly and remove the dependencies of the signals inside it.
- The standard IO and even the standard error reports should be closed for that daemon.
- After creating it, the parent has to leave and the child process should not be related to any other processes.

# [1:25:41](https://youtu.be/Vdo7wd0_obM?t=5141s) Writing a Daemon

The speaker explains how to write a daemon in programming.

- Start with a fork and remove all dependencies with the terminal.
- If opening a device, assign standard input and output related to those devices.
- Clear standard input and outputs using figure close those descriptors.
- Refer to file descriptions for the device being worked on using two.
- Change current working directory to proper weight most of the time is root directory is required.

# [1:27:04](https://youtu.be/Vdo7wd0_obM?t=5224s) Becoming A Daemon

The speaker daemonstrates how to become a daemon using old ways.

- Remove STD in STD or STD out and go to related file descriptors divided on dev whatever that thing is even devnale is important for us because it's when it's null device so output/input should not be written anywhere that's worst case scenario
- Start with fork and put yourself at background
- Default action in here is action of parent which just takes out and goes out
- Child will remove all dependencies with terminal, become leader of session
- Change modes, change current working directory to root directory
- Open/close all files and remove all file dependencies
- Make sure maximum number of files that can be open is set to something and everything is done
- Put yourself in the background and close it

# [1:30:30](https://youtu.be/Vdo7wd0_obM?t=5430s) Daemon Creation

The speaker explains how to create a daemon.

- Open file descriptor.
- Get rid of all those on standard input and output.
- Using dope 2, map standard input/output stuff to whatever requirements of this daemon are needed.

## [1:33:08](https://youtu.be/Vdo7wd0_obM?t=5588s) Wrestler and Acronyms

- The speaker mentions a wrestler.
- The speaker talks about controlling Arctic terminal.
- The speaker mentions acronyms related to communication.
