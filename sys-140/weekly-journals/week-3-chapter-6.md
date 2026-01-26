# Week 3: Chapter 6

## Memory Management

Memory Management is the process of dividing up memory so that it is accessible to programs and applications.

\
<br>

| Type of Management Technique | Description                                                                                                                                                                                                                                                               |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Partitioning                 | Divides memory into sections. Each section is called a partition. Each section can be assigned to programs. This process can be done physically or virtually.                                                                                                             |
| Fixed Partitioning           | The physical memory card is split into partitions (rather than virtually meaning that the computer doesn’t split it up after the fact).                                                                                                                                   |
| Variable partitioning        | Allows the size of partitions to be modified during runtime, allowing for better memory management.                                                                                                                                                                       |
| Virtual Memory               | Virtual memory is essentially fake memory. The computer assigns a program a virtual memory space that might look like a “contiguous” piece of memory, but in actually that memory might be fragmented. This allows the computer to be more efficient in its memory usage. |
| Paging                       | Paging is a form of partitioning in which memory is split into equal-sized pages, named “page frames”. When loading applications, it finds empty page frames to load the applications and updates the page table (essentially a memory registry within memory).           |

<br>

### Memory Management Requirements

<br>

* Protection: All memory must be protected from modifications. All processes running in memory should be checked before they run!&#x20;
* Relocation: All programs might be in various areas of memory.&#x20;
* Sharing: Multiple processes need to be able to run in the same area of memory without protection mechanisms interfering.&#x20;
* Contiguous vs. Non-Contiguous: Programs organized sequentially vs. Programs might be in any place in memory based on&#x20;

<br>

Segmentation is a memory management technique that allows for memory protection by assigning permissions and a set length to memory sections. Each memory segment is allowed to do certain things set by its permissions and can’t exceed its length. (From what I know, if they exceed their length, it’s considered a buffer overflow?) There are three types of segments: Code, Data, and Stack.

<br>

## Process Management

The CPU executes and handles processes. Any program that does an action on a computer is handled by the CPU as a process. Processes will require other resources like memory, files, or other devices connected to the motherboard. Most processes, user and operating system processes, can run in parallel.

<br>

The operating system manages user and system processes, suspending or resuming processes, synchronizing processes, and ensuring processes aren’t blocked or stopped by certain actions.

<br>

There are multiple ways to define what a process actually is. It could be an instance of a program currently running, but it is defined as an “executing program.”&#x20;

<br>

Program - Group of instructions

Process - Activity as a result of instructions. This means that a process is a result of a program.

<br>

Working in combination with hardware, Operating Systems are the managers of all processes. You can imagine the Operating System as a manager ensuring that all processes are running properly, efficiently, and using the right resources. Processes may be assigned to different processors, with different amounts of RAM, etc. Operating systems need to be able to create, stop, control, schedule, interrupt, synchronize, and manage processes. (Think more puppet master.)&#x20;

\
<br>

| Process State | Description                                                                                                                                                                                                        |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Executing     | Currently running and is using processing power                                                                                                                                                                    |
| Waiting       | A process that is waiting for a processor to become available to run                                                                                                                                               |
| Blocked       | A process that is waiting on some sort of information (I/O) before it can run. For example, it might not have the information it needs from another chained process. (Not sure if that’s the correct terminology.) |
| Suspended     | A process that can run, but the OS hasn’t put it in the queue.                                                                                                                                                     |
| Ready         | The process has been placed in memory and will eventually execute.                                                                                                                                                 |

The OS keeps track of all the processes in a table called the Process Table, or Process Control Block, or Switch Frame. It contains basic information about the processes, including their numbers, states, their memory bounds, what CPU registers they may be using, and other actions that the process might be conducting.&#x20;

<br>

Threads split up programs into multiple pieces so that they can run in parallel. If a program uses more than one thread, it is called Multithreaded. Multithreading allows them to work on similar pieces of data to be more efficient. This is for multiple reasons, including allowing the programmer to switch between processes and even switch threads without kernel overhead. For a heavier program, it can’t separate its processes, making it slower.&#x20;

<br>

“A process that uses threads does not get more CPU time than an ordinary process” (What the heck does this part mean ???)

### Scheduling

Scheduling is how the operating system “controls the order in which the work to be done is completed.”

<br>

Throughput is the amount of work done in a certain amount of time.&#x20;

\
The end goal of scheduling is to make the system run as efficiently and fast as possible, making it a core operating system function. Operating systems need to balance many different needs, including running as many processes as predictably as possible without wasting too many resources, while also ensuring higher priority programs run first. It needs to ensure that resources are available in case of a higher-priority process needing to be run. When a system is overloaded, it also needs to be able to throttle its processes so it doesn’t fail horribly and crash your system.&#x20;

## Textbook

For computers to run properly, they need to be able to quickly store and access data. They use this with RAM (Random Access Memory). There are two types of RAM: DRAM and SRAM. SRAM, standing for Static RAM, is what the CPU uses for its cache, and DRAM, standing for Dynamic RAM, is what we think of when we talk about RAM sticks in our computer. DRAM slowly loses information (in 1s and 0s) over time, which is why it needs to be refreshed as it runs.&#x20;

\
<br>

| Term                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Synchronous DRAM       | Fast memory access. It coordinates with the CPU to prep data on the bus before the memory it's replacing is even executed and removed from RAM.  Allows for faster speeds.                                                                                                                                                                                                                                                                                                                          |
| DDR (Double Data Rate) | Double Data Rate stands for RAM that can transmit twice during a clock cycle, allowing it to have double data speeds. Different module types include DDR2, DDR3, DDR4, and DDR5. The lower the number, the slower the RAM speed. DDR2 and DDR3 utilize 240-pin connectors, whereas DDR4 and DDR5 use 288-pin DIMMs. In addition, DDR4 and DDR5 operate at lower voltages while also maintaining higher speeds, making them much more efficient. (Also expensive too, but we don’t talk about that.) |

<br>

All RAM cards are the same size as one another, though they are not compatible, as they have different pin configurations.

<br>

Understanding memory speeds is simple. For example, if a website says a RAM stick is DDR5-4000, that means it transmits at 2000 MHz (half) on the front side bus. Because it transmits twice with Double Data Rate, it says 4000.

\
<br>

| Memory Feature                                     | Description                                                                                                                                                                                                                                                                                                                                     |
| -------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Non-Parity                                         | The RAM stick does not error-check. Look for parity or ECC if you want a stick that checks for errors.                                                                                                                                                                                                                                          |
| ECC                                                | A mathematical algorithm that checks for errors in memory. Detects up to 4-bit memory errors.                                                                                                                                                                                                                                                   |
| Unbuffered Memory vs. Buffered Memory (Registered) | <p>Unbuffered memory is memory that moves immediately through the memory chip for processing without checks.</p><p><br></p><p>Buffered Memory is placed in registers in the RAM module to check for accuracy before being transmitted, and it is slower than unbuffered memory. Look for Fully Buffered DIMMs if you want a chip like this.</p> |
| Serial presence detect (SPD)                       | A module within the memory chip that contains information (and sometimes heat sensors) about itself so that the BIOS can read it and use that information.                                                                                                                                                                                      |
| Dual-voltage memory                                | A memory chip that can run at a lower voltage to generate less heat. Basically, underclocking for RAM.                                                                                                                                                                                                                                          |
| Extreme memory profile (XMP)                       | Settings in the BIOS that allow for memory overclocking. (XMP is amazing)                                                                                                                                                                                                                                                                       |

These features are not mutually exclusive.

<br>

Windows Disk Caching - Doesn’t exist in this version

To monitor the memory used in Windows, you can look at Task Manager using Ctrl + Shift + Esc and clicking into “Performance.” It will contain basic information about your RAM on your computer, including how much is in use, how much is available, etc.&#x20;

<br>

Modified memory needs to be written to a hard drive or SSD before it can be used. Standby memory is memory that is cached. Committed RAM is the amount needed by processes to function, out of the total available memory.&#x20;

\
Paged Pool - Memory used for operating system processes and device drivers that are non-essential.

Non-Paged Pool - Memory used for operating system processes and device drivers that is essential and cannot be removed.&#x20;

<br>

Hardware Reserved is for drivers or other firmware that cannot be accessed by Windows or the Operating System.

<br>

Flash memory is solid-state memory that doesn’t lose its data when it loses power. It’s used in mobile devices, SSDs, digital cameras, etc. Flash memory doesn’t need to be refreshed, meaning it doesn’t lose or corrupt data as often. You may know flash memory by its use in USB flash drives, which can be used to transfer data offline. Data is read from flash drives using a memory card reader, which is embedded into most, if not all, computers and devices.&#x20;

## Guiding Questions

Based on the number of applications you typically run and the amount of physical RAM on your system, do you think your personal computer should use a larger or smaller page file?

<br>

I’m honestly not sure. For the most part, I really don’t use that many applications on my computer, and most of them are pretty lightweight in terms of resource usage. I currently have 32 GB of RAM on my computer, and so I’ve never really hit that cap. For the most part, I think my page file is big enough, and that I don’t need any more or less. I’ve got plenty of space, and plenty of RAM.&#x20;

<br>

Have you ever had issues with a program using excessive amounts of memory or disk space and slowing down your computer? If so, how did you identify and solve the problem?

<br>

On my laptop, the AI engine uses up a boatload of my RAM. I identified the issue by looking at the task manager when I first started up my PC. I saw at least 10 RecallProcesses and 1 RecallProcessManager. I tried ending the processes, but that didn’t work, as it seems they had persistence. I tried everything from modifying registry keys to messing with policies and drivers, but to no luck… It doesn’t slow down my computer, but it uses up memory even though I have recall turned off. :(

\
<br>
