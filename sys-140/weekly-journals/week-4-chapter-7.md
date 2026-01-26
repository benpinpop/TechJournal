# Week 4: Chapter 7

## Storage Methods

Data is placed into file blocks. The way that happens is described as allocation.

### Contiguous Allocation

Contiguous Allocation is the simplest way to store data on a hard drive or other container, determining the maximum size the file could possibly be, and setting that as a limit. It then stores that data and the maximum length it could be on the disc. (Probably not very efficient).

### Linked List Allocation

Linked List Allocation stores data in blocks, in which each block contains a memory pointer to the next file block. The benefit is that files can grow with “incremental allocation,” rather than overwriting files in contiguous allocation. The downside is that because the files aren’t contiguous, read speeds suffer. The longer the linked list, the worse performing it is. In addition, if a file block is corrupted and a pointer leads to nothing, you don’t know where the rest of the file is.

### Segment-Based Allocation

Segment-based allocation splits the file into multiple contiguous blocks, storing the information in a table. This is more beneficial than contiguous allocation because it has more flexibility, and it also takes less disk time. On the off chance that the disk becomes fragmented, the segment table might need to be as big as each data entry itself. Aka, one table entry for each file block, which is problematic. Random access isn’t as fast because it’s split into different contiguous blocks.&#x20;

![](<../../.gitbook/assets/unknown (25).png>)

<br>

### Indexed Allocation

Indexed allocation stores the locations of each individual block in an index (an array), assuming a declared maximum file size. The indexed list contains enough indexes (space for pointers), as the declared maximum. Indexed allocation allows for fast access, but data is fragmented across the disk. The downside to that is the farther away the data is stored from each other, the less the performance.&#x20;

“Also, as a file increases in size, the file system needs to reallocate the index array and copy old entries.” (Does this mean the file can go over the maximum size?)

<br>

### Multilevel Indexed Allocation

Multilevel indexed allocation is like indexed allocation, but later pointers point to arrays of more pointers. For example, the first 12 pointers would point to regular data blocks, whereas after that, the 13th pointer points to a single indirect block, aka a block pointers that point to data blocks. The 14th pointer might point to a double indirect block, which has pointers that point to more pointers, that then point to data. This type of allocation is useful for both sizes of files, as the small files are accessible through the first pointers, and larger files can be accessed with the indirect pointers. Downsides include the fact that the indirect block pointers don’t provide information about what data they’re holding.&#x20;

<br>

![](<../../.gitbook/assets/unknown (26).png>)

### Inverted Allocation

Inverted allocation is primarily used in backups where storage space is the main concern. Inverted allocation functions by hashing the file content and placing it in the data block. This allows data in different blocks of the same content (with the same hash) to share the same data block. This is extremely efficient and allows for saving as much space as possible.&#x20;

## Secondary Storage Methods

We need the computer to run programs, and this is done by executing programs held in storage. Best case scenario, this is all in RAM, but RAM is too small and volatile for that, so the data is held in secondary storage.&#x20;

### Disk Structure

Disks give us most of the secondary storage (besides SSDs, USB Flash, NVMe, and Tape).

<br>

* A disk platter (the physical disk) is divided into several tracks.
* Each track has several sectors.
* Each platter has two surfaces, top and bottom.
* A cylinder is the set of tracks.
* To access a sector, you need to know:
* Drive Number
* Track/Cylinder
* Surface
* Sector

![](<../../.gitbook/assets/unknown (27).png>)

![](<../../.gitbook/assets/unknown (28).png>)

### Disk Performance

The operating system handles the disks and how they function and allocate space, ensuring that they run efficiently.&#x20;

<br>

Disk Bandwidth - # of bytes transferred / Amount of time between transfers

<br>

Access Time - Finding Data (Seek Time) → Moving the Heads/Readers to the surface → Rotating the disks to the sector required (Latency Time).

<br>

No seek time is needed when accessing a track from the same cylinder. (What does it mean by electronically moved to the next surface)

### Access Time

Seek time takes an average of 5-10ms. Latency time takes an average of 3ms and depends on the disk’s rotational speed (5,400 - 10,000 rpm). Floppy disks have a slower rotational speed, meaning their latency times are around 100 - 200 ms. Transfer time is dependent on the data being transferred.

### Disk Space Management

Disks must have their space managed properly; they can’t just have their data stored randomly. Data is stored in block sizes. The larger the blocks, typically, the more fragmenting there is. The smaller the blocks, the harder the disk has to work to fetch and write data. Disks are concerned with efficiently using disk space and the speed of accessing the files.&#x20;

<br>

Disks also keep track of the free space with a list; this is done in three ways.&#x20;

<br>

In Bitmaps, storage space is indicated by 1s and 0s. A 1 means the space is taken, a 0 means that the space is open. Searching through bitmaps can be slow, even though they help find contiguous free blocks. They also take up a lot of space (like 25% of space…)&#x20;

In Linked Lists, pointers are stored pointing to the free blocks until the last pointer becomes NULL. This allows for a quick search to find free space.

In a free sequence list, disks record a pointer to the first free block of every sequence, as the data is stored contiguously. This means we just need to know the number of blocks used. This is more efficient in contiguous allocation, but has the downside of more disk fragmentation.

### Disk Scheduling

First Come First Serve (FCFS) - Self-explanatory.&#x20;

Shortest-Seek-Time-First (SSTF) - The request that requires the shortest time to find is executed first.

SCAN Scheduling - The disk arm scans the entire disk, handling requests as it sees them (if a request requires a certain part of the disk that it’s passing over, it does), and then it reverses and goes back.

Circular Scan (C-Scan) - Same as SCAN Scheduling, but it moves back to the beginning of the disk and handles no requests on the return trip.

Circular Look (C-Look) - The disk arm goes as far as the last request requires it to in both directions, and then reverses after instead of going to the end. (This seems most efficient)

## Textbook

Storage Devices Overview

Data is stored in numerous ways, most commonly on physical devices. (Optical, Hard Drive, Flash) Data can also be stored in the cloud, transmitted over the internet, and stored on physical devices off-site, called cloud storage.&#x20;

\
Hard Drives can be placed internally in PCs or connected externally via multiple types of connectors (USB, SATA, etc.) Hard Drives have much higher capacity than RAM, in the terabytes, and serve as the primary computer storage. Hard drives come in multiple form factors, from 5.25 - 1.8 inches. Hard drives are not exclusive to HDDs; they also include SSDs.

<br>

In magnetic hard drives, disk arms read from disk platters, using magnets. There are two arms per platter, reading both bottom and top, allowing it to write data to the disk. The platters are rotated at a set speed (depending on the drive) from 5,400 RPM to 15,000 RPM, which is proportional to the read and write speed. The faster the platter rotates, the more operations the HDD can do. When a reading head touches a platter, something called a “head crash” happens.&#x20;

<br>

Hard Drives end up failing after a long time, which is indicated by their Mean Time Between Failures (MTBF) statistic. This is why you need backups. Disks and their platters are extremely sensitive, even to dust or particles (like CDs), which is why you should keep it enclosed at all times.

![](<../../.gitbook/assets/unknown (29).png>)

<br>

### SSD Overview

SSDs (Solid State Drives) are much faster than Hard Drives by using non-volatile flash memory, which is much smaller, faster, cooler, and doesn’t require any moving parts, eliminating the main point of failure for HDDs. The downside is that SSDs are much more expensive, which has resulted in hybrid SSDs, hard drives with SSDs in them. This allows for faster data to be stored on the SSD, and less-used data less used can be pulled from the HDD.

### Hard Drive Interfaces Overview

<br>

Hard Drives need to be able to operate with rules. Imagine each hard drive has its own internal operating system that handles its operations and how it transmits data. Integrated Drive Electronics (IDE, AT Attachment, Enhanced EIDE) are often found in home drives, Small Computer System Interface (SCSI) is most often found in server drives. IDE and SCSI started the same way as parallel architectures, but SCSI allowed for more devices to be connected.&#x20;

<br>

Parallel architecture sends “multiple bits over multiple paths,” whereas serial architecture goes from device to device, with a single link, allowing for easy scalability. For the most part, modern drives use serial architectures.&#x20;

<br>

Serial ATA (SATA) and Serial SCSI: Serial Attached SCSI (SAS) are used. In general, most drives are SATA drives.\
\
NAS - Network Attached Storage

SAN - Storage Area Network

<br>

In general, NAS drives run faster, storing data for multiple servers and are meant to be in use 24/7.

### Hard Drive Preparation Overview (but ONLY look for the following definitions: cluster, sector, cylinder)

Cluster - “Smallest amount of space reserved for one file”

Sector - Several sectors make up a cluster.&#x20;

Cylinder - Cylinder already defined above.&#x20;

<br>

![](<../../.gitbook/assets/unknown (30).png>)

### Fault Tolerance

Fault Tolerance is the ability of a storage device to keep running after a drive fails. This is done using a RAID (Redundant Array of Independent Disks) array. RAID arrays are implemented with hardware (the drives) and software (the BIOS), and can be enabled in the BIOS. There are different levels of RAID and the fault tolerance it provides (0,1,5,10). RAID is also accessible through Windows Software for better accessibility and control. In addition some drives have “nested” RAID, which allows for different RAID levels on different drives.&#x20;

\
<br>

| Raid Level | <p><br></p>                                                                                                                                                                                                                                                                                         |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0          | Also called Disk Striping, RAID 0 ensures different parts of data are on two or more drives to increase system speed. It does not provide fault tolerance or help when data fails.                                                                                                                  |
| 1          | Also called Disk Mirroring, RAID 1 ensures copies of data are on two or more drives with the use of a disk controller on the off chance that a drive fails. Duplexing uses two disk controllers, which results in slower write speeds. (Why does disk mirroring not result in slower write speeds?) |
| 0+1        | Titled 0+1, it RAID 01/0+1 uses mirroring and striping (combined) at the same time, needing a minimum of four hard drives, with an even number of disks. Read times are quick, but write times are slower.                                                                                          |
| 1+0        | The same thing as RAID 01/0+1, but instead of combining mirrored and striped sets, they are separate in RAID 10.                                                                                                                                                                                    |
| 5          | RAID 5 uses disk striping with parity (extra information), writing copies of data to 3+ drives in case another drive dies.                                                                                                                                                                          |

<br>

RAID drives are “hot swappable,” meaning they can be switched out even with the power on. (how???)

## Guiding Questions

Have you used cloud storage in the past? Do you prefer local or cloud storage of your data? Explain your answer.

I have used cloud storage, but mostly for document storage like Google Docs. I typically prefer local storage for most of my files because it's faster and easier to use, and I don’t have to download them. Cloud storage is useful, but my files also aren’t important enough to warrant full cloud storage backup.&#x20;

<br>

Do you think adding more platters to a hard drive increases or decreases its mean time between failures (MTBF)?

I feel like it would probably decrease the mean time between failures because you need more heads to read the platters, and therefore, a higher chance of one of the heads breaking or failing. The failures are mostly dependent on the moving parts, so more moving parts mean more chance of failure.&#x20;

<br>
