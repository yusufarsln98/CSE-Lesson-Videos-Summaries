# CSE 344 | 3rd Week | 14.03.2023-L1

## [0:00:02](https://youtu.be/dmNAR2767AE?t=2s) Introduction to Files in Unix

Overview: In this lecture, we will be discussing files in Unix operating systems. We will cover the basic operations that can be performed on files such as opening, closing, reading and writing to them. Additionally, we will discuss special I/O operations that can be done using ioctl.

* Everything in a Unix or Linux system is represented as a file.
* Directories are files containing the names of other files within them.
* Devices such as monitors, CPUs, printers and USB disks are also represented using files.
* Pipes and sockets are important for inter-process communication.

### [0:01:29](https://youtu.be/dmNAR2767AE?t=89s) File Implementation in Linux

* The `ls` command can be used to view the status of a file.
* The structure of files on a typical Linux system includes directories such as `/etc`, `/bin`, `/home`, and `/lib64`.
* User directories are located in `/home`.
* Libraries specific to 64-bit systems are located in `/lib64`.

### [0:03:11](https://youtu.be/dmNAR2767AE?t=191s) Types of Files

* Devices are represented using files and owned by the root user.
* Pipes and sockets can also be represented using files.
* External drives can be mounted directly to the system and accessed through the file system.

### [0:05:18](https://youtu.be/dmNAR2767AE?t=318s) Structure of Files on a Typical Linux System

* Directories include `/etc`, `/bin`, `/home`, and `/lib64`.
* User directories are located in `/home`.
* Libraries specific to 64-bit systems are located in `/lib64`.
* `/bin` contains common Linux functions such as `ls`, `kill`, and `cp`.

## [0:07:29](https://youtu.be/dmNAR2767AE?t=449s) Understanding File Paths

Overview: In this section, the speaker explains how to locate files on a system using file paths.

* The path is how you locate your files on a system.
* You can access files using absolute or relative paths.
* Two special directories are used to access other files from your current directory: "." and "..".
* Examples of accessing files using both absolute and relative paths are given.

### [0:09:26](https://youtu.be/dmNAR2767AE?t=566s) File Descriptors

Overview: This section covers the three file structures that the operating system uses.

* The operating system uses three file descriptors for each file generated on a terminal.
* These are standard input (represented by FD 0), standard output (represented by FD 1), and standard error (represented by FD 2).
* When you want to input something to the file, it uses the standard input. If you want to output something from the file, it will use the channel of standard output. If an error occurs, it will publish it on something called standard error related to that file.

### [0:10:32](https://youtu.be/dmNAR2767AE?t=632s) Basic Functionality of Files

Overview: This section covers some basic functionalities of the file system.

* Everything is a request to the operating system kernel.
* To open a file descriptor in order to work with the file over the device, you start with a path and give some flags and mode.
* The flags are either read-only, write and read, create, or append. Truncate means discard previous content and start writing at beginning.
* If -1 is returned from this open function call, there's an error either in calling flags or mode or going into that path is not possible.
* When you're done writing, you close the file descriptors.

## [0:14:28](https://youtu.be/dmNAR2767AE?t=868s) Understanding Permissions

Overview: This section covers how to set permissions for different groups of users in a file.

* Use the `chmod` command to set permissions for a file.
* The three groups of users are the owner, group, and everyone else.
* Permissions can be set for read, write, and execute access.

### [0:16:07](https://youtu.be/dmNAR2767AE?t=967s) Using `open()` Function

Overview: This section covers how to use the `open()` function to create and modify files.

* Use the `open()` function with appropriate parameters to create or modify a file.
* The mode parameter specifies the read, write, and execute permissions for each group of users.
* Always close files after using them to prevent resource leaks.

### [0:19:17](https://youtu.be/dmNAR2767AE?t=1157s) Writing Files

Overview: This section covers how to write data into a file using Python.

* Use the `write()` method with appropriate parameters to write data into a file.
* The return value is the number of bytes written into the file.
* Always check for errors when writing into a file.

### [0:20:15](https://youtu.be/dmNAR2767AE?t=1215s) Example - Adding Timestamps

Overview: This section provides an example of adding timestamps to a file using Python.

* Use the `time` module to get current time information.
* Open the desired file with appropriate permissions using `open()`.
* Write timestamp information into the end of the file using `write()`.

## [0:21:48](https://youtu.be/dmNAR2767AE?t=1308s) Writing to a File

Overview: In this section, the speaker demonstrates how to write to a file in Python.

* When calling the function again and displaying its contents, another timestamp is added to the end of the file.
* Running the program consecutively will append to the end of the file due to an argument.
* This is how you write stuff to a file.

### [0:22:29](https://youtu.be/dmNAR2767AE?t=1349s) No Content

There is no content in this section.

### [0:22:45](https://youtu.be/dmNAR2767AE?t=1365s) No Content

There is no content in this section.
