# Week 2: Chapter 3

## A+ Chapter 3 | 9/2/25

## Processors

<br>

Processor (Central Processing Unit (CPU)): Conducts all the main processing and computing for the computer, handling inputs and instructions.&#x20;

<br>

There are a variety of manufacturers, including Samsung, Intel, AMD, etc. Any company that makes a device like Apple or Samsung likely makes its own CPU. There are two different processor architectures: 32-bit and 64-bit. This denotes the size of data it can compute and communicate with.&#x20;

<br>

ARM processor: Typically used on mobile devices like phones, laptops, or computers. ARM stands for “Acorn RISC (reduced instruction set computing)”&#x20;

<br>

Motherboards typically only take one type of processor, so an AMD processor motherboard will not be compatible with an Intel processor motherboard.

<br>

Processor speeds are measured in gigahertz (GHz), with one hertz being one cycle of a CPU. Processors use binary, using what are called data buses to transport data. There are two types, internal and external. The internal bus is inside the CPU, used for transporting data around the CPU, whereas external data buses allow the transport of data to other devices on the motherboard, like a GPU or printer. The larger the data bus, the more data can be transferred.

\
\
<br>

| Component of CPU            | Explanation                                                                                                                          |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Arithmetic Logic Unit (ALU) | Handles all math, calculations, and comparisons.                                                                                     |
| Control Unit                | Handles all processes inside the CPU.                                                                                                |
| Registers                   | Stores any data in binary inside the CPU for quick usage. The closer the data is to the CPU, the faster it can be accessed and used. |
| I/O Unit (Input/Output)     | Handles data entering and exiting the CPU.                                                                                           |

<br>

CPUs can be sped up by increasing clock speed, changing the architecture to reduce intermediary steps, or increasing the number of internal buses. (This makes sense, but at the same time not at all in terms of “intermediary steps").\
\
Processors don’t always run at maximum speed due to code limitations, power considerations, and hardware issues. Processors can also overclock, increasing their max clock speed for harder tasks.&#x20;

<br>

Clock speed: “The speed of the processor’s internal clock, measured in gigahertz.”

Front side bus: The speed between the CPU and specific motherboard parts in megatransfers per second (MT/s)

Backside bus: “The speed of data between the CPU and the L2 cache located outside the main CPU but on the same chip.” (Not sure what it means by same chip, but outside the CPU…)

PCI (Peripheral Component Interconnect) bus speed: The speed of data on the PCI bus. 33 and 66 MHz are typical speeds. (up to 533 MB/s)\
PCIe (Peripheral Component Interconnect Express) bus speed: The speed on a PCIe bus. PCIe busses are significantly faster than PCI.&#x20;

AGP: Accelerated Graphics Port, an outdated architecture for transporting data between GPUs.

CPU throttling: When a CPU runs at a lower clock frequency than normal to lower energy use and/or heat. Helpful for when a CPU is overheating or using too much power.

<br>

CPUs run on a clock cycle system, transferring data 4 times each cycle. Older CPUs typically transfer once during a clock cycle. &#x20;

<br>

The CPU cache is the fastest form of data storage for the CPU, as it is closest to the actual chip/hardware.

\
<br>

| Cache Number | Description                                                                                                        |
| ------------ | ------------------------------------------------------------------------------------------------------------------ |
| L1           | Located directly inside the processor, provides the fastest access to data.                                        |
| L2           | Not directly a part of the CPU, but it is in the packaging (On-die cache). (What does this mean in the packaging?) |
| L3           | Located in the CPU housing or on the motherboard. Typically, stronger processors have this cache.                  |

\
<br>

Thread: “Small piece of an application process.”\
Multithreading: Allows multiple threads to run different processes, thereby increasing efficiency.

Hyperthreading: This technology enables multiple threads to run in parallel. (What’s the difference?)

<br>

Extra Research:

Hyperthreading is at the hardware level and uses a single core, whereas multithreading requires multiple physical cores and can be at the software or hardware level.&#x20;

[https://www.baeldung.com/cs/multithreading-vs-hyperthreading](https://www.baeldung.com/cs/multithreading-vs-hyperthreading)&#x20;

<br>

Transferring data between the L2 Cache and the motherboard used to be a bottleneck, slowing performance. This problem\ was fixed with the implementation of the front and back side buses. You may think that having a faster CPU means a faster computer, but that doesn’t take into account bottlenecks. You may have a super-fast CPU, but your motherboard might not be able to keep up, limiting your performance.&#x20;

<br>

Most CPUs nowadays have multiple cores, meaning they have more than one chip in their physical housing, allowing them to run more processes.

## Graphical Processors

<br>

Graphical Processing Unit (GPU): A dedicated card for processing graphical effects that a CPU might not be equipped to handle.\
\
Integrated GPU (iGPU): A graphics card integrated into the CPU, typically not nearly as good as a dedicated GPU. For example, you might see “Intel HD Graphics” on a laptop sticker. (From personal experience.)

<br>

While GPUs are dedicated to graphics processing, there are also GPGPUs, standing for General Purpose GPUs. These help the CPU process some of the workload of the computer, lowering the strain on your CPU.&#x20;

## Virtualization

Multiple processor cores allow computers to run virtual machines, independent machines isolated from your computer environment. These are helpful for remote access machines, or for running and testing malware you might not want on your computer.&#x20;

## Processor Manufacturers

AMD and Intel and the most dominant companies selling CPUs on the market right now. (Intel is definitely sliding, though.) Each company names their CPUs with family names, for example, Ryzen 9, 7, 5, 3, or Intel Core i9, i7, i5, etc. These provide broad general categories to understanding the capabilities of the CPU.&#x20;

<br>

## CPU Sockets

CPUs will slot into a unique socket in the motherboard. Each motherboard has a different type of socket, like AM4, AM5 (which is a set of CPUs that will fit). Some motherboards may even be multisocketed, allowing them to have different types of CPUs, though this is rare for personal computers. (From personal experience.)

## Cooling

Processors use lots of energy; as a result, they create a lot of heat, requiring cooling. This is solved by using a heat sink, a metal block that allows the transfer of heat to a device that cools it. There are typically two sets of devices used: water cooling and fan cooling. A fan will attempt to cool the heatsink down by bringing air through it, while a liquid cooler uses water, transferring heat to a radiator, which is then cooled by fans. Both are highly effective in cooling CPUs in combination with thermal paste. Thermal paste is a substance that goes between the CPU and heatsink, allowing them to make optimal contact and transfer as much heat as possible into the heatsink. It essentially fills in the microscopic holes in the CPU so that those surfaces are connected to the heatsink.&#x20;

<br>

(I’ve never heard of phase-changing cooling, I assume that requires a liquid to )

<br>

## Chipsets

I’m still confused. (?????) From what I read, the chipset is another electronic component that helps the memory, CPU, and motherboard communicate with each other, but isn’t that what the buses do? Or is it that the buses are just the lanes of communication, and the chipset coordinates the talking? Anywho, questions for class.

<br>

Sources Used:

[https://www.lenovo.com/us/en/glossary/chipset/](https://www.lenovo.com/us/en/glossary/chipset/)&#x20;

[https://en.wikipedia.org/wiki/Chipset](https://en.wikipedia.org/wiki/Chipset)&#x20;

## Guiding Questions

## The chapter portrays pipelines as an unquestioned benefit, but can you think of any downsides to pipelining, or any scenarios where pipelining may not be effective?

Pipelining might be a disadvantage if you run out of bandwidth. It may be an effective strategy for sending data across the motherboard, but it could come with its downsides. When I was building my own computer, my motherboard stated that if I used one of my PCIe slots, the other slot would have downgraded speeds. From what I assume, this means that there were limited PCIe slots.

<br>

Consider the tasks you typically use your personal computer for. Would you benefit more from increasing the amount of cache/RAM (faster access, but more expensive) or disk storage (slower, but cheaper)?

<br>

I personally would benefit from neither. I run 32 GBs of 3600 MT/s, and have a total of 5 TBs in storage on my computer. Most would benefit from RAM upgrades, as they can always free up storage space if needed, but RAM is highly dependent on what applications you’re running. (again, from personal experience). If you have 100 Chrome tabs open and you only have 16 gigabytes of memory, then you’ll want more RAM.&#x20;

<br>
