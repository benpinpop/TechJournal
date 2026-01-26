# Week 5: Chapter 11

## Notes

### Design Overview

To design a computer, you need to be able to understand what you’re talking about. You need to understand the parts, and how specifically they work together. At a minimum, you need to be able to explain what a part does to another person. At the highest level is applying this understanding and troubleshooting it with analysis.&#x20;

### Computer System Design

#### Graphic/CAD/CAM Design Workstations

Graphic Workstations typically work with computer-aided design (CAD) and computer-aided manufacturing (CAM) for engineering or industrial design related purposes. These applications are pretty heavy weight and require a lot of computing.&#x20;

\
<br>

| System Part | Requirement                                                    |
| ----------- | -------------------------------------------------------------- |
| CPU         | Powerful Multicore                                             |
| RAM         | Maximum amount                                                 |
| Storage     | An SSD with multiple large drives                              |
| GPU         | High-end video card with a large amount of VRAM                |
| Display     | Large or Dual Display                                          |
| Peripherals | Other devices might include tablets, scanners, or 3D printers. |

<br>

#### Gaming PCs

Gaming PCs are typically for personal use, mostly being utilized for video games. Video games tend to be very graphics and CPU intensive. Gaming PCs have many of the same requirements of a Graphic Design workstation, but with a few caveats to accommodate for the higher end processing. Gaming PCs might require a sound card and speakers, extra system cooling, an SSD (NVMe possibly), quality peripherals including a mouse and high refresh rate monitor.

<br>

#### Audio/Video Editing Workstations

A/V Workstations are specifically designed for Audio or Video editing and require large amounts of storage and RAM. Specifically, A/V workstations require specialized sound cards as well.

<br>

| System Part | Requirement                                             |
| ----------- | ------------------------------------------------------- |
| CPU         | Powerful Multicore                                      |
| RAM         | Large amount                                            |
| Storage     | Fast large capacity Hard Drive                          |
| GPU         | High-end video card with a large amount of VRAM         |
| Display     | Dual Display                                            |
| Peripherals | Other devices might include a digital tablet or scanner |

(Why doesn’t the textbook order them by part, good lord)

#### Network-Attached Storage (NAS) Devices

A network attached storage device is a singular device that contains multiple hard drives for storing information. Typically NAS devices are used in a home setting to hold extra storage or file share to other devices on the network. Some NAS devices use SSDs rather than hard drives.The only requirement is a NAS container, and drives for it.

#### Virtualization Workstations

Virtualization workstations are used for simulating different operating systems in virtual machines. Virtualization workstations have at least one operating system running at a time and require extra amounts of RAM and Processing.\
<br>

| System Part | Requirement                                                             |
| ----------- | ----------------------------------------------------------------------- |
| CPU         | Max CPU Cores (12+ cores)                                               |
| RAM         | Max RAM (Like 96 GB)                                                    |
| Storage     | Multiple fast large capacity hard drives or SSDs                        |
| NAS         | Optional, helpful for sharing files like system images across a network |

<br>

#### Thin Client Workstations

Thin Clients are base computers that run all their processes from a server rather than handling the processes themselves. Typically they are equipped with a good network card, a display, basic peripherals, and low-end components. These are used in industrial, commercial, or corporate settings when information needs to be centralized or compartmentalized. Typically files are stored on a storage area network and cost much less than other workstations. Because the processes are run from the server, it allows for easier control.

#### Thick Client Workstations

Thick clients are your typical laptop and are equipped for handling basic tasks such as Microsoft Word and use of the internet. These workstations meet the minimum requirements for the operating system and might have other applications installed like Word, or Excel. Dual Monitors are optional but recommended in some cases. (Only if it’d be beneficial to productivity.)

#### Home Servers

A home server is a multiuse server used for a variety of purposes, serving as storage, sharing files, printing, streaming, as backup storage, etc. Home servers can even be accessible outside of the local network. Home servers typically have hard drives with RAID setup, a strong Networking Card (1 Gb/s NIC - Networking Interface Controller), multiple processors (or multicore processor), 8 GB+ of RAM, and other installed applications to execute the servers core function.&#x20;

<br>

Also, make sure that you’re thinking about the environment, because many of the parts have green certifications, etc. Check ENERGY STAR for energy efficiency ratings, and the EPA for it’s EPEAT score.

### Motherboard and Associated Component Design

The motherboard and its chipset determine the type of CPU you can use. If you have an AM4 chipset, you must use an AMD AM4 CPU, you cannot use an Intel CPU on an AMD Chipset. The chipset also determines the type (e.g. DDR4, DDR5) and amount (e.g. 32, 64, 96, 128 GB, etc) of memory, and speeds (e.g. 3600 MT/s) that the system accepts. The end goal is to use as much channelling as possible for the motherboard as that increases system performance and speed.

<br>

Each motherboard comes with its own specifications, make sure to check what features it has and what parts come with it already! Compatibility is extremely important.&#x20;

### Storage Subsystem Design

The storage subsystem design is how you design your storage system within your workstation. There are a variety of different types of storage, hard drives, SSDs, USB, etc. When considering how to design your storage system, all you care about is what the customer wants. Specifically, how much storage, how fast they need that storage, and how long they plan on using this system before upgrading it. (Because god knows they will wait for as long as possible to upgrade)

<br>

Different storage types have different external or internal connectors, sizes, speeds, technologies, and more.&#x20;

<br>

### Troubleshooting Overview

Troubleshooting is a vitally important skill when working in IT as the more time someone is unable to work due to an issue, the more money cannot be earned by the company. (And that is the key goal, money!!!) You have to use all the tools you possibly can to fix a system, and be as determined as possible. The first step is to identify the issue. Then, create a theory based on the issue, test the theory, create a plan to fix the problem and implement the plan and ensure the plan worked. (VERIFY!!!) Finally, document the issue and the solution for anyone who comes across the issue in the future.

<br>

The user does not know what they’re doing, have them give you replication steps. Even if they complain about issue X, it may in fact be issue Y. Ensure you ask questions in a non-threatening or accusatory manner so that they don’t withhold information. Ask questions that are open ended to get an understanding, and closed ended questions (yes-no) to narrow down the possibilities. Check the obvious, like the power button, etc, back up your data beforehand, and even if the problem can’t be recreated doesn’t mean it didn’t happen.

<br>

When identifying the cause of the issue, look at everything. Does the monitor load? Are the keys outputting on the screen, does the mouse work? If it’s not booting, is the power on, is the power switch on the power supply turned on? Ask all the questions. Check system logs, motherboard display lights, and document any information you can to identify the cause.&#x20;

<br>

## Guiding Questions

<br>

Based on the chapter, what are the three most important components to think about if you were building a computer for yourself? How about if you were building a computer for another family member?

\
If I was building a computer for myself, I’d prioritize the CPU, RAM, and GPU. While the motherboard is an extremely important part, most motherboards have what anyone needs, and no one really needs an extremely expensive motherboard unless they are doing extreme overclocking, or they need an overkill amount of PCIe slots/busses. For storage, you can get a 1 TB M.2 NVMe for under $100, so it’s not that big of a deal. The CPU and RAM make or break the system, and the GPU adds gaming and other processing functionality. For a family member, I’d likely prioritize the same thing, though if gaming wasn’t a concern, I’d either look at storage or the motherboard rather than a GPU.&#x20;

<br>

Think back to the last time you had to troubleshoot a problem with your computer. What steps did you follow? Did you follow a different set of steps than the book recommends, and if so, do you think following the book's steps would have worked out better or worse?

<br>

The last time I had to troubleshoot an issue with my computer was when I was building it. It was on the first test boot, and we were checking power and display. (I was building it with a friend). I plugged the display in, and the display said “Input Not Supported.” We googled the issue online and it seemed to be a graphics issue. We checked a variety of reddit threads… I found a piece of paper in the GPU box that said “Driver Disc not included in this product,” so we thought it was a driver issue, and that the GPU did not have the proper drivers installed for the specific monitor. Our first step was to find a different monitor to see if that one would work. We plugged in a different monitor, and it worked! As soon as we could, we installed internet and graphics drivers. For the most part, we followed the steps of the textbook, identified the issue, and came up with a solution. I didn’t really document the issue, but I have photos saved. Honestly, I think I troubleshooted pretty well and my computer is still functional and working to this day.&#x20;

\
\
\
<br>
