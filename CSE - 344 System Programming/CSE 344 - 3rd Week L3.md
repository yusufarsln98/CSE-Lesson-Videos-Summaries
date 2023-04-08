# CSE 344 | 3rd Week | 14.03.2023-L3

## [0:00:02](https://youtu.be/52XadFbFN9Q?t=2s) Introduction

Overview: The speaker introduces the topic of file manipulation and redirection in Unix systems.

### [0:00:06](https://youtu.be/52XadFbFN9Q?t=6s) Recording an Idea

* The speaker briefly mentions recording an idea.

### [0:00:30](https://youtu.be/52XadFbFN9Q?t=30s) Functions Required for File Manipulation

* The speaker discusses the functions required to open, close, read, write, and perform special operations on a file.
* They mention redirecting the results of a file from one place to another using redirection.

### [0:01:14](https://youtu.be/52XadFbFN9Q?t=74s) File Descriptions for Reading and Writing

* The speaker explains that there are three file descriptions that are open - one for reading, one for writing, and one for error.
* Two of them are buffered while one is not buffered.
* They discuss how to redirect the output of one file descriptor to another or write the contents of a file to another file.

### [0:02:05](https://youtu.be/52XadFbFN9Q?t=125s) Redirection Using Terminal

* The speaker demonstrates how to redirect outputs using ">" and ">>" signs in terminal.
* They explain that 0 is used for input, 1 is used for output, and 2 is used for standard error.

### [0:03:19](https://youtu.be/52XadFbFN9Q?t=199s) Pipe Symbol

* The speaker explains how the pipe symbol works in Unix systems.
* They demonstrate how it connects standard output to standard input.

### [0:05:19](https://youtu.be/52XadFbFN9Q?t=319s) File Representation on Unix Systems

* The speaker explains that file representations on Unix systems are done using something called an index node or I node.
* They mention that the size, owner, and timestamp of a file are put on the header of it with the block count and some blocks just directly point to the data.
* They discuss how files are buffered and stored on disk.

### [0:06:59](https://youtu.be/52XadFbFN9Q?t=419s) Directory Implementation

* The speaker explains that directories are also files but they do not contain any data.
* They mention that directory implementation is different from file implementation.

## [0:08:10](https://youtu.be/52XadFbFN9Q?t=490s) Copying Files and Hard Links

Overview: This section discusses how copying files and creating hard links work in an operating system.

* Copying a file from one directory to another on the same disk only changes the necessary entries under each directory file, without physically copying it.
* If the file is on separate physical partitions, it needs to be buffered and copied before other operations happen.
* Changing a file name only requires changing the corresponding directory entry, not physically copying it.
* Hard links allow multiple files to point to the same place on disk, saving space. If contents don't change, increasing the number of links associated with that file is all that's needed.

### [0:08:49](https://youtu.be/52XadFbFN9Q?t=529s) Copying Files

* Moving a file deletes it from its original location and puts it in the destination directory.
* Copying a file from one location to another copies its content to the new location.
* Operating systems buffer copy operations if they are on separate physical partitions.

### [0:11:01](https://youtu.be/52XadFbFN9Q?t=661s) Hard Links

* Hard links allow multiple files to point to the same place on disk, saving space.
* Increasing or decreasing the number of links associated with a file is all that's needed if contents don't change.
* The `ln` command can be used in command line arguments for generating hard links.
* Removing a link can be done using `unlink`.

## [0:15:12](https://youtu.be/52XadFbFN9Q?t=912s) Understanding Undelete and Soft Links

Overview: This section covers the concepts of undelete and soft links.

* Most operating systems have an undelete feature that increments the associated link count to one, making the file available for recovery.
* If another process has used the space, data may be lost.
* Soft links are created using ln -s and create a new file that points to the initial file.
* Soft links have a size on disk while hard links do not.

### [0:17:23](https://youtu.be/52XadFbFN9Q?t=1043s) Temporary Files

Overview: This section covers temporary files and their usage in logging.

* Temporary files are used when there is limited space on stack or heap.
* They can also be used for logging purposes.
* To create a temporary file, use mkstemp with a template string.
* Once you have a file descriptor, you can perform normal read/write operations on it as if it were a regular file.
* It is good practice to remove temporary files once they are no longer needed.

### [0:20:27](https://youtu.be/52XadFbFN9Q?t=1227s) Changing File Status with stat and fstat

Overview: This section covers how to change the status of files using stat and fstat.

* The five status steps include last time accessed, last time modified, creation time, owner/group permissions, and type of file.
* These statuses can be changed using stat and fstat commands.
* Even timestamps can be changed which makes them unreliable.

## [0:22:54](https://youtu.be/52XadFbFN9Q?t=1374s) Changing File Display and Hidden Files

Overview: In this section, the speaker explains how to change file display and access hidden files.

* Be careful when changing file types as unexpected outcomes may occur.
* The command "ls -l" displays all files except for hidden files.
* Hidden files are denoted by a dot at the beginning of their name.
* To display hidden files, use the command "ls -al".
* Hidden files contain configurations specific to certain programs and are normally not meant for users to access.

### [0:26:34](https://youtu.be/52XadFbFN9Q?t=1594s) Unlinking Files and File Descriptors

* After using the unlink operation, the file disappears from its location but still has file descriptors that can be used.
* Other users will not be able to see what is happening with the file.
* The amount of data that can be written on a file is limited by the associated buffer size given to standard input and output.
* This limits your ability to write large amounts of data on a file because it is not actually on disk.

## [0:28:55](https://youtu.be/52XadFbFN9Q?t=1735s) Miscellaneous Topics

Overview: This section covers various topics briefly mentioned by the speaker.

* No content provided.

## [0:33:12](https://youtu.be/52XadFbFN9Q?t=1992s) File Descriptive Tables

Overview: This section discusses the three file descriptive tables that are used by the operating system for each process.

* The inode table is a system-wide table that everyone can access.
* The file open table contains all open files with their stats.
* Each process has a file descriptive table specific to itself.

### [0:33:46](https://youtu.be/52XadFbFN9Q?t=2026s) Opening Files with Processes

* Processes A and B have file descriptive tables specific to themselves.
* Each process can open multiple files.
* Two processes might have two file descriptors pointing to the same file on the open file table.

### [0:34:12](https://youtu.be/52XadFbFN9Q?t=2052s) Accessing Same File from Different Processes

* Two different processes might be trying to access the same file on the inode.
* Two or more of a process's file descriptors might be pointing to the same database on the open file system.

### [0:35:13](https://youtu.be/52XadFbFN9Q?t=2113s) Three Possible Scenarios

Three things can happen when two or more processes try to access the same inode:

1. One process tries to use another's file descriptor
2. Two processes try to open the same thing
3. Both are trying to open an existing one while someone else is accessing it

### [0:38:13](https://youtu.be/52XadFbFN9Q?t=2293s) Buffering and File Descriptors

Overview: This section explains buffering and how it relates to standard input, output, and error.

* When creating or accessing a file, three file descriptors are associated with the process: standard input, output, and error.
* The kernel uses buffering to speed up read and write operations instead of going to the hardware for each operation.
* Increasing buffer size reduces CPU usage but has a limit where further increases do not provide any advantage.
* Modern operating systems use buffers instead of direct read/write operations to the disk or other devices.

### [0:40:17](https://youtu.be/52XadFbFN9Q?t=2417s) Buffering in Operating Systems

Overview: This section discusses how modern operating systems use buffering.

* Instead of direct read/write operations, modern operating systems use buffers.
* Buffers can cause issues when processes terminate before flushing their buffers.

## [0:41:58](https://youtu.be/52XadFbFN9Q?t=2518s) File Operations and Buffering

Overview: This section discusses file operations and buffering in C programming.

* Use after either the file descriptor that uses the error or flash them using FF flash for that specific file.
* All right operations and read operations that are buffered will be written on the desk or redirect the read operation will be done from the disk.
* Most buffering is done on writing anyway.
* C's implementation of using the file is a little bit different than what we actually use. It uses a specific structure called "file" to handle all of them.
* You can use either of them, using either the file structure or just deal with those fds by yourself, whichever you prefer.
* Instead of using open and close, you have to use f printfs f scanf f get output f instead of read and write.
* You can rely on the operating system and just do read and write, whichever you want to use.
* The buffer size can be extended using set buffer if you need your buffer to be higher or lower than standard.
* If you don't want to use any buffering, if you just want to flush over everything that you read that have written on but if you want to make sure that what you have used for writing is written on the disk just got to flash it over there I use FF flash to write contents of buffer directly to disk.

### [0:43:46](https://youtu.be/52XadFbFN9Q?t=2626s) Buffering in C Programming

Overview: This section continues discussing buffering in C programming.

* If you use C library this is ones you want to use if you use stdo write and read is what going stack with now
* The buffer size can be extended using set buffer if you need your buffer to be higher or lower than standard.
* If you don't want to use any buffering, if you just want to flush over everything that you read that have written on but if you want to make sure that what you have used for writing is written on the disk just got to flash it over there I use FF flash to write contents of buffer directly to disk.

### [0:45:05](https://youtu.be/52XadFbFN9Q?t=2705s) Conclusion

Overview: This section concludes the lecture.

* Even a flash FF Flash, the flashing operation is sent as a request to the kernel so the kernel will synchronize its contents with the actual disk because even in the time of SSDs accessing hardware and writing the disk takes a lot of time compared to operations done on actual memory.
* End of this week's lecture.
