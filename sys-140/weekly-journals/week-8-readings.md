# Week 8: Readings

## [Introduction to Operating System](https://www.geeksforgeeks.org/operating-systems/introduction-of-operating-system-set-1/)

allocatingThe Operating System is the base program that bridges the gap between Hardware and Software, allowing you to execute core functions on the computer. Everything runs on top of the OS, with the OS allocating all materials, input, and processing.

![](<../../.gitbook/assets/unknown (53).png>)

<br>

Operating Systems aren’t just UIs; they have Command Line Interfaces, and Graphical User Interfaces (CLI and GUI). Command Lines use terminal windows, and GUIs use icons and menus, and are more user-friendly. At the core of an operating system is the Kernel, which handles all processes, memory, file, and device management. If you imagine an OS like an onion, the Kernel is the innermost layer.&#x20;

<br>

The primary goals include making the use of a computer user-friendly, executing programs, ensuring resources are properly distributed and allocated, and protecting the system from unwanted access, like malware. (CIA triad!)

<br>

Secondary goals include making sure resources are allocated efficiently and that the system runs reliably.&#x20;

<br>

Back to the onion metaphor, the outermost layer is the Shell, handling and taking input from the user. This would be something like Command Prompt, or Powershell, or the Terminal in Linux. The Kernel is still our innermost layer.

<br>

The most common operating systems include Windows, Mac, Linux, and Unix.

<br>

## [The Kernel](https://www.geeksforgeeks.org/operating-systems/kernel-in-operating-system/)

The kernel acts as a bridge between software and hardware, managing resources. It connects I/O like keyboards and handles all tasks. Even though the Kernel is the core, the operating system provides more key functions like a UI, file system, networking, and other utilities to make a functional, useful system. If you want an example, the kernel is like the manager of everything; it knows what to do, when to do it, and how to do it.&#x20;

![](<../../.gitbook/assets/unknown (54).png>)

<br>

There are several kernel types: monolithic, micro, hybrid, nano, and exo.&#x20;

<br>

Monolithic kernels have all OS services running in the kernel. It’s fast, but has less fault tolerance. Microkernels have most services for the user to access, rather than being in the kernel; It’s reliable, but has more overhead. Hybrid mixes monolithic and microkernel, mixing speed and safety by isolating some services. Nanokernels are extremely small and handle the most basic of things, giving most services to the user. Exokernels give apps direct control over hardware (scawy).

<br>

The Kernel handles processes, memory, device management, file systems, resources, security and access control, and communication between processes.

<br>

The kernel is the first thing that loads, and it has special privileges, also known as kernel mode. This allows the kernel to access hardware resources and stop the user from messing up their own computer.&#x20;

<br>

To make requests to the kernel, applications use system calls (software interrupts), with the kernel executing the operation requested by the application. The kernel gives a result, and ensures that its multitasking is properly. (Yay!)

## [File Systems in Operating System](https://www.geeksforgeeks.org/operating-systems/file-systems-in-operating-system/)

File systems are systems that allow you to organize and access your data on storage devices (SSD, USB, HDD, etc). Applications request file operations (File Explorer), like reading, writing, or deleting. The Logical File System handles metadata, directories, permissions, and file names, so that the user application knows what to display. From there, you access the Virtual File System to access to Physical File System, which holds the storage data on physical media.&#x20;

![](<../../.gitbook/assets/unknown (55).png>)

There are a variety of different types of file systems, from FAT, NTFS, ext, HFS, and APFS. You may notice NTFS, which is currently used by Windows. FAT is a little older, and HFS/APFS are used on Mac and iOS.

![](<../../.gitbook/assets/unknown (56).png>)

File systems handle space management on your mediums, moving files, defragmenting, and more.&#x20;

\
A file directory is a file that contains information and data about files on your system like location. Directories file systems actually organize your files.&#x20;

<br>

There are numerous file types, all with different extension names (e.g. .exe, .obj, .bat), used to indicate to your operating system what application should execute it. This information is stored in directories.

<br>

There are different types of directories, single-level, two-lelvel, and tree-structured. In single, there’s one directory for all users, in two there’s a directory for each user, and tree has the directory like a tree, allowing you to group files together better. There are also different file allocation methods, see past journal.

<br>

File systems keep track of how much space is free on your disk, using a a variety of methods from Bit tables, free block lists, linked lists, or boundary tags.

## [Serial Vs. Parallel Transmission](https://www.geeksforgeeks.org/computer-networks/difference-between-serial-and-parallel-transmission/)

Serial transmission is a way of sending data that is one-by-one, whereas Parallel transmission sends data in parallel, i.e., multiple pieces of information at a time. Serial transmission is simpler, but can be slower than parallel transmission.

<br>

8 bits are sent at one time, in order (with different timing), including a 0 (start) and 1 (end) as a parity bit. Serial transmission uses a 9-pin cable.

<br>

Serial transmission is very useful across long distances.&#x20;

<br>

![](<../../.gitbook/assets/unknown (57).png>)

<br>

Parallel transmission sends multiple bits at the same time, rather than in order.&#x20;

![](<../../.gitbook/assets/unknown (58).png>)

It is much faster than Serial, even though it is more complex, working much faster over shorter distances. Parallel transmission cables use 25-pin ports, containing 17 signal lines and 8 ground lines. (What are ground lines? Where can I find these?) The 17 signal lines are split into 4 start signals, 5 talking lines for errors, and 8 for transferring data.&#x20;

<br>

Some key differences:\
\
Parallel transmission is more expensive than serial transmission. Parallel sends eight bits in a clock pulse compared to one clock pulse for serial. Converters are required for serial communication.

\
“Parallel transmission is unreliable and complicated.” (Well then…)

<br>
