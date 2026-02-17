# Mid Term Studying

## Types of Storage Media

* Magnetic media
  * Hard disks and tapes
* Flash memory
* Optical

## HDD Form Factors

3.5, 2.5, 1.8

SATA - Card Edge

PATA/IDE - Pin connector

SCSI - Small Computer System Interface

* Multiple variants, 50-pin or 68-pin molex. 80-pin

SATA vs. SAS (Serial Attached SCSI) - SAS has wider spacing between pins

IDE - Slowest

SCSI - Slow

SATA - Faster

SAS - Fastest

Disk Platter, two sides for each platter. Tracks hold multiple sectors. A cylinder is a group of tracks that can be read at the same time.

Disk capacity: Cylinders x Heads x Sectors/Track x 512 B/sector

Sectors also contain basic info, ID info, synchronization fields, and ECC

Fragmentation, when files are stored far apart

SSDs are better, but have over write process, read-erase-modify-write cycle. Blocks must be erased; you cannot erase pages or sections.

TRIM command

* File deletion

Over provisioning

* Saving space just in case cells fail

Slack space - Leftover data

Logical vs. Physical: Physical is entire drive, logical is just the data inside the partition.

Forensic Image Formats

* dd (raw)
  * Raw copy, no cryptographic hashes, or error handling, no logging or compression
* E01 (metadata)
  * Lots more features
  * Metadata is stored within the image itself, harder to modify
* FTK Smart, AFF (haven't touched)



Evidence Acquisition

* No mistakes allowed
* Have to take an image on evidence or else it is contaminated.
* Copy vs. Image: Image has metadata, copy doesn't
  * Also is bit for bit
* Chain of Custody
* Hashes to validate evidence
* Live Acquisition
  * Memory, unencrypted data, passwords, open entwork connections
  * Contamination issues?
* Static
  * Machine is off
* Local vs. Remote
  * Local has physical access
  * Remote is over network tools

Write Blockers

* Software
* Hardware
