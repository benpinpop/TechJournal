# 1/13/26: Lecture One

## Summary

## Overview

* HDDs
* Current Technology
* Disk Drive Basics
* SSD, SDD vs HDD, SSD internals
* Forensics on HDD and SSDs.

## Storage Media

* Magnetic media
  * Hard Disk Drive (HDD)
    * 2 years before you start losing data
  * Tapes
    * Used for archives
    * 15-20 years before you start losing data
* Non-volatile memory (flash)
  * Solid State Drive (SSD)
  * Universal Serial Bus (USB) Drive
* Optical media

## HDD Form Factors

* 3.5", 2.5", 1.8" by width
* SATA (card edge connector) vs. PATA (pin connector, no backing)
  * PATA is older

## SCSI (Small Computer System Interface)

* Similar to VGA connectors
* Also called "Scuzzy"
* Uses molex connectors, 50, 68, and 80 pin interfaces.&#x20;

## PATA/IDE Interface

* 40-pin connectors, with a 39-pin interface
* **IDE drive jumper options**
  * Master
  * Slave
  * Cable select
* IDE - Integrated Drive Electronics

## Current Tech

* SATA - Serial Advanced Technology Attachment
* SAS - Serial Attached SCSI
  * Wider gap between interfaces

## Media Speeds

| Technology | Speed                   |
| ---------- | ----------------------- |
| IDE        | 133 Mb/s                |
| SATA       | 1.5 Gb/s - 16 Gb/s      |
| SCSI       | Various, up to 320 Mb/s |
| SAS        | 3 Gb/s - 22.5 Gb/s      |

## Disk Drive Basics

The spindle spins the disks in a circle while the actuator arm reads and writes, moving back and forth. The head makes contact with each side of each platter.&#x20;

Disk Platter - Round and flat, magnetic, or ceramic discs in a hard drive that hold the data

Each platter has two sides, and each hard drive can have multiple platters

A track is a concentric circle where all information is stored.

Modern disks contain 10k tracks; each platter has the same number of tracks.

Track numbering starts from 0 and starts from the outside of the platter. Each group of the hard drive is called a sector.&#x20;

All heads are going to be on the same track number. The number of cylinders equal the number of tracks.

Capacity = Cylinders x Heads x Sectors x sector\_size

Logical Block Address (LBA)

## Platters

* The more platters, the more storage
  * Gaps between each disk decreases
  * More susceptible to vibrations and surface imperfections
* Increase the area density on each track rather than making more platters
  * We've reached the limit of bits

## Sectors

* Physical unit of hard drive storage
* Like a bucket
* Usually 512 bytes with overflow for drive control
  * ID information (Sector # and status)
  * Synchronization fields
  * ECC (Error correcting code)
* Size has increased to 4096 (4 kilobytes)
* Bad Sectors
  * Areas that are not useable
  * Causes
    * Excessive read/writes
  * Viruses
  * Voltage surges
* Identifying bad sectors is defect mapping

## Fragmentation

* Hard Drives write data to the disk wherever it is closest, resulting in file fragmentation.
  * Fragments of files are scattered around
  * Reassembling files is defragmentation

## SSDs (Solid State Drives)

* Good things
  * No mechanical parts, all circuit boards and storage chips
  * Constant seek time (even for random access)
  * File fragmentation is not an issue
  * No spinup time, fast startup
  * No noise, and lower power
* Problems
  * Overwriting is expensive
    * read-erase-modify-write
  * Limited life cycles
  * Data recovery and carving issues
  * Power faults can lead to data loss
* Info
  * Data is written in blocks and pages
  * LBAs exist
  * Writing is fast, but to overwrite, you have to erase
  * You have to erase the entire block which is around 1 MB
  * Move data to RAM, erase, and then write
  * SSDs breaking down over time
  * Wait for data to get copied into the buffer, erased, and changed
* Optimization Methods
  * When editing a file, you mark a page as stale, and then the empty page after holds the data
* Garbage collection
  * Removing all the stale pages

### TRIM Command

* ?

### Over-provisioning

* Limited reads and writes
* Extra capacity not accessible
* Used to avoid wearing out storage cells

### Forensics on HDD & SSDs

* Problems with imaging data from HDD and SSD
* How can you access deleted files
* Types of encryption

## Unpartitioned vs. Unallocated

* ?

## Slack Space

* Extra space leftover in a sector from a file
