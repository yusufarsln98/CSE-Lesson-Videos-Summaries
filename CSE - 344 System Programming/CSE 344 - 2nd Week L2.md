# CSE344 - 2nd Week Lecture 2

## [0:00:02](https://youtu.be/FQ1VUzs5TYM?t=2s) Introduction

Overview: The video discusses how the operating system allocates resources to processes using virtual memory management.

### [0:00:21](https://youtu.be/FQ1VUzs5TYM?t=21s) Resource Allocation

- The operating system gives each process a resource location in both user space and kernel space.
- Modern operating systems use virtual memory management because it is impossible to put all processes in physical memory.
- Virtual memory management uses a structure called virtual memory, which is not on physical memory but on a virtual thing.
- Special or temporary locality enables the efficient use of system resources by each process.

### [0:03:11](https://youtu.be/FQ1VUzs5TYM?t=191s) Uninitialized Static Variables

- Uninitialized static variables are initialized after they are initialized.
- When compiling a program, all uninitialized variables are put at the top of the list of instructions.
- When forming the process, all uninitialized data segments are put into corresponding places.

### [0:04:36](https://youtu.be/FQ1VUzs5TYM?t=276s) Virtual Memory Management

- The kernel maintains page tables for each process that correspond to virtual addresses.
- The kernel knows where exactly that portion of the memory is on the physical system (RAM or hard drive).
- If you access a memory space that you're not supposed to access, an error signal occurs.
- Virtual memory management puts an abstraction between actual hardware and foreign memory.

## [0:08:38](https://youtu.be/FQ1VUzs5TYM?t=518s) Controlling Heap and Stack

Overview: The video discusses how to control the allocation of extra space for Heap and Stack.

- There are two variables, program break and top of stack, that can be changed to grow Heap from one side.
- By changing the value of the top of stack, the size of the stack can be increased.
- Two ways to allocate extra space for Heap and Stack are using malloc or alloca.

### [0:10:12](https://youtu.be/FQ1VUzs5TYM?t=612s) Inputs and Environment Variables

- The portion on inputs and environment variables required for a process is initialized.
- Arc C and arcv arguments in the main function determine how many arguments will be there in arc V.
- Environ is a global variable used to access environment variables.

### [0:14:12](https://youtu.be/FQ1VUzs5TYM?t=852s) Changing Execution of Process

- There is a way to change execution of a process by changing variables located in inputs and environment variables before program execution starts.
- Get my environments set my environments unset my environments or clean my environment are functions that allow you to change, overwrite, or display your environment setups.

### [0:15:44](https://youtu.be/FQ1VUzs5TYM?t=944s) Allocating Extra Space for Heap and Stack

Overview: To allocate extra space for Heap and Stack, program break, top of stack, and heap must be adjusted.

- Adjusting program break up allows you to use unallocated memory for Heap.
- Adjusting top size downward allows you to use unallocated memory for Stack.
- Keeping track of program break is important as it affects collisions between Stack and Heap.

## [0:17:29](https://youtu.be/FQ1VUzs5TYM?t=1049s) Memory Allocation with Malloc

Overview: In this section, the speaker discusses memory allocation using malloc and its family functions.

- Instead of using BRK and SBRK, we use malloc and its family functions to allocate memory.
- With malloc, you don't have to decide on where the system breaks sizes. You just request a portion of memory for your variable.
- The system will change the size of that portion in the background and allocate extra memory for your application.
- Freeing allocated memory is easier with malloc as it eases the process, especially for threaded programs.
- Using malloc makes it easier to keep track of the allocation and deallocation of memory.

### [0:18:52](https://youtu.be/FQ1VUzs5TYM?t=1132s) How to Use Malloc

- Malloc is easy to use; you give a size, and if that much space is available, the system will give you that portion of memory.
- When you're done with that portion of memory, use the free function to put the system break back into its position before making the malloc system call.
- Not freeing allocated memory can cause stack collisions or prevent other executions in your process from using that portion.

### [0:20:19](https://youtu.be/FQ1VUzs5TYM?t=1219s) Importance of Freeing Allocated Memory

- Some programmers tend not to use free when their program executes foreign code or terminates. However, freeing allocated memory is essential as it allows other processes to use those portions.

## [0:28:45](https://youtu.be/FQ1VUzs5TYM?t=1725s) Special Call for Allocating Memory

Overview: In this section, the speaker discusses a special call for allocating memory.

- It is possible to allocate memory without calling free using a special call.
- This call changes the placement of the allocated memory but does not require freeing.
- The top of the stack changes when this function executes and allocates memory.
- Malloc family functions not only use this portion but also request extra memory from the kernel, causing the whole portion to grow. Therefore, it is essential to free that memory when done using it.

## [0:30:04](https://youtu.be/FQ1VUzs5TYM?t=1804s) Conclusion

Overview: In this section, the speaker concludes their discussion on allocating memory.

- The speaker has covered everything associated with allocating portions of memory for each process.
- There are virtual memory segments and related things with yep (special call).
- A little portion of data exists in Kernel space too.

## [0:31:25](https://youtu.be/FQ1VUzs5TYM?t=1885s) Q\&A Session

Overview: In this section, the speaker opens up for questions from students.

- The speaker left time for students to ask any questions they may have.
- No specific questions were asked during this session.

## [0:31:41](https://youtu.be/FQ1VUzs5TYM?t=1901s) End of Section

Overview: This section marks the end of a segment in the lecture.

- No new information was presented in this section.
