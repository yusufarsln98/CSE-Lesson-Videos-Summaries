# CSE344 | 1st Week | 28.02.2023-L1

## [0:00:04](https://youtu.be/Q8f5nw2EnIY?t=4s) Introduction and Condolences

Overview: The instructor introduces himself and expresses condolences for those affected by recent earthquakes.

* The instructor welcomes the students to CSE 344 System Programming.
* He expresses his condolences to those who have lost loved ones in the recent earthquakes.
* Life must go on despite the tragedy.

## [0:00:32](https://youtu.be/Q8f5nw2EnIY?t=32s) Class Structure and Technical Difficulties

Overview: The instructor discusses the structure of the class and technical difficulties with online learning.

* This is a typical class, but there are some strange things going on.
* Technical difficulties arise as he shares his screen to show the syllabus.
* They have been given five hours for this course, which is too much. They need to cut at least two hours from it.
* Online learning can be boring, but they will find a way to make it work.

## [0:01:24](https://youtu.be/Q8f5nw2EnIY?t=84s) Overlapping Courses

Overview: The instructor discusses overlapping courses and how they may affect scheduling.

* Some students' schedules overlap with another course (machine learning).
* If students write to him about their overlapping schedules, they may be able to adjust accordingly.

## [0:02:31](https://youtu.be/Q8f5nw2EnIY?t=151s) Course Materials

Overview: The instructor discusses required and supplementary materials for the course.

* The main book is "Unix and Linux System Administration Handbook" published in 2010.
* There are also four supplementary books that students may use, but he recommends only using the first two.
* Chapters in the syllabus correspond to chapters in the main book.
* The course will last for 14 weeks, with the final week left for review or the announcement of a final project.

## [0:04:26](https://youtu.be/Q8f5nw2EnIY?t=266s) Attendance and Grading Policy

Overview: The instructor discusses attendance and grading policies for the course.

* Attendance is required (80% minimum), but it may be difficult to enforce online.
* This is a project-based course, so there are no last-minute exams to save students from failing.
* Project-based courses must be taken seriously.

## [0:06:08](https://youtu.be/Q8f5nw2EnIY?t=368s) Conclusion

Overview: The instructor concludes his introduction to the course.

* The course is not very hard, but some parts may be tedious and require a lot of energy.
* Students should take this course seriously and pass it.

## [0:06:51](https://youtu.be/Q8f5nw2EnIY?t=411s) Attendance Policy

Overview: The speaker criticizes the university's attendance policy and emphasizes the importance of attending class.

* Failing a course once and not attending it means you will fail again.
* The person who created this rule is stupid.
* There are more than 200 people in the class, but less than 40.

## [0:07:48](https://youtu.be/Q8f5nw2EnIY?t=468s) Grading Policy

Overview: The speaker explains the grading policy for the course.

* 80% attendance is required.
* Homework is worth 30% of the grade.
* Midterm project or exam (not yet decided) is worth 30% of the grade.
* Final exam is worth 40% of the grade.
* If you don't attend three out of five homework assignments, you fail.
* Minimum requirement for final exam is getting a 40 out of 100.

## [0:09:22](https://youtu.be/Q8f5nw2EnIY?t=562s) Importance of Following Rules

Overview: The speaker emphasizes that students should follow the rules strictly to avoid failing.

* Don't try to bend or scratch these rules; they will be followed strictly.
* Even if you do well on homework or midterm, if your final grade is below 40, you fail.
* More than 200 people are in this class; take warnings seriously.

## [0:10:08](https://youtu.be/Q8f5nw2EnIY?t=608s) Syllabus Overview

Overview: The speaker provides an overview of what will be covered in the course syllabus.

* C programming language will be used for everything in this course.
* Memory management, garbage collecting, and cleaning up will be done by the student.
* Learning curve is steep but worth it.

## [0:12:15](https://youtu.be/Q8f5nw2EnIY?t=735s) Aim for High Grades

Overview: The speaker encourages students to aim for high grades.

* It is possible to get an A in this class.
* Don't aim for the lowest grade; aim for the highest grade you can achieve.

## [00:30:19](https://youtu.be/Q8f5nw2EnIY?t=1819s) Introduction to Operating Systems

Overview: This section introduces the concept of operating systems and their main function, which is to allocate resources for processes.

* Operating systems are also known as system level programming interfaces.
* The core of an operating system does more than just scheduling processes.
* Modern operating systems allocate resources for processes and enable multiple executions to share computer resources without interrupting each other.

### [00:31:09](https://youtu.be/Q8f5nw2EnIY?t=1869s) Components of an Operating System

* An operating system consists of a kernel and standard software tools like compilers, interpreters, graphical user interfaces, file utilities, and editors.
* The kernel manages and allocates system resources and processes generated by multiple users.
* The part that does the scheduling is called the kernel.

### [00:33:00](https://youtu.be/Q8f5nw2EnIY?t=1980s) Functions of the Kernel

Overview: This section explains what the kernel does in an operating system.

* The kernel schedules processes, manages memory for processes, uses disk so that usage is hidden from users, creates and terminates processes, accesses other devices, handles networking, and maintains ways to approach itself.
* Process scheduling is when more than one process can run simultaneously on a system.
* Preemptable means that everything a process needs to access hardware is determined by the kernel itself.

### [00:35:11](https://youtu.be/Q8f5nw2EnIY?t=2111s) Preemptable Multitasking Operating System

Overview: This section explains what preemptable multitasking means in an operating system.

* A preemptable multitasking operating system allows more than one process to run simultaneously on a system.
* The kernel takes those programs and uses the necessary alignments that they can use the CPU memory and all that stuff, disabling the usage of other processes.
* Preemptable means that when a process accesses hardware, it is determined by the kernel itself.

## [0:37:41](https://youtu.be/Q8f5nw2EnIY?t=2261s) Memory Management and Virtualization

Overview: In this section, the speaker discusses how the kernel assigns hardware resources to programs and manages memory through virtualization.

* The kernel assigns corresponding CPU and hardware resources to the program that is running.
* When multiple programs are running, even high memory will not be sufficient. Therefore, the kernel puts an abstraction called virtual memory in place.
* Virtual memory manages the hard way through virtualization so that every process has its own isolated memory segment on the virtual memory.
* Each execution has its own isolated memory segment on the virtual memory that may not correspond to a direct memory segment on actual hardware.
* The kernel provisions file systems so that users do not directly access disks when creating or deleting files. Instead, they communicate with disks via a file system.

### [0:38:34](https://youtu.be/Q8f5nw2EnIY?t=2314s) Direct Memory Access

* The user does not need to keep everything that the execution needs in memory at all times.
* Only necessary components of the memory from virtual numbers to actual RAM are used when executing processes.
* Context switching occurs whenever another execution is decided to run on use the CPU. Everything will be switched, and only necessary parts of only specific executions will be in-memory.

### [0:39:56](https://youtu.be/Q8f5nw2EnIY?t=2396s) Provision of File Systems

* Users do not directly access disks when creating or deleting files; instead, they communicate with disks via a file system.
* The kernel decides how much portion of data is actually on disk; users do not know what's going on with actual disk.

### [0:41:24](https://youtu.be/Q8f5nw2EnIY?t=2484s) Process Creation and Termination

* Every program that is compiled and put into a form that can be understood by the CPU creates a process.
* Necessary adjustments are made in memory on the kernel's databases so that processes can be created.
* When an execution is completed, all resources have to be released and freed, which is done by the kernel.

### [0:42:38](https://youtu.be/Q8f5nw2EnIY?t=2558s) Accessing External Devices

* There is an abstraction layer between hardware and user level determined by the kernel when accessing external devices.
* Scheduling occurs when more than one process wants to do the same thing at the same time.

### [0:43:02](https://youtu.be/Q8f5nw2EnIY?t=2582s) Task Networking

Overview: In this section, the speaker discusses how packages are sent to other computers on networks.

* Packages are taken, saved, and sent whenever the kernel thinks it is suitable.
* Access to every device is determined by the kernel itself.

### [0:44:20](https://youtu.be/Q8f5nw2EnIY?t=2660s) Multi-user Operating Systems

Overview: In this section, the speaker discusses how multi-user operating systems work.

* The kernel has to manage tasks independently such that each user will not be affected by whatever another user does.
* Each process created by requesting the kernel should not affect each other or other processes created by other users on the system.

## [0:45:47](https://youtu.be/Q8f5nw2EnIY?t=2747s) User Mode and Kernel Mode

Overview: The user mode is where programs are written and run, while the kernel mode handles requests for system resources. Manipulating what goes on inside the kernel is called the kernel space.

* Programs are run in user mode
* Requests for system resources are handled by the kernel mode
* Manipulating what goes on inside the kernel is called the kernel space

### [0:46:50](https://youtu.be/Q8f5nw2EnIY?t=2810s) Using Multiple CPUs

* Modern computers use more than one CPU at a time
* We can let the core of the operating system know that we want to use more than one CPU at a time
* We can arrange to run processes using multiple CPUs simultaneously

### [0:47:48](https://youtu.be/Q8f5nw2EnIY?t=2868s) Inter-process Communication

Overview: When there are multiple processes running at once, it's important to let them communicate with each other. This is done through inter-process communication.

* Two processes can communicate with each other through inter-process communication
* Communication is done through the kernel, not directly accessing another process's resources
* Signals can be used to know about a process's state or terminate/kill other processes running

### [0:50:03](https://youtu.be/Q8f5nw2EnIY?t=3003s) Inter-process Communication vs File System

Overview: While file systems can be used for inter-process communication, it's often more efficient to use inter-process communication directly.

* Inter-process communication is often more efficient than using file systems for communicating between processes
* Some forms of inter-process communication use file systems (pipes, fifos)

### [0:50:53](https://youtu.be/Q8f5nw2EnIY?t=3053s) Processes Operating in Isolation

Overview: Processes operate in isolation and cannot directly communicate with each other. Requests to create or end processes are handled by the kernel.

* Processes operate in isolation and cannot directly communicate with each other
* Fork is a request to the operating system to create a new process that is identical to the requesting process
* Requests to end processes are handled by the kernel, not directly by the requesting process
