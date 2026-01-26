# 1/23/26: Evidence Acquisition

* What to do when acquiring evidence
  * Maintain Chain of Custody (CoC)
  * Maintaining the integrity of evidence
  * Make observations, take notes
  * Photograph everything
  * Store Evidence
    * A paper bag for wet items to let them dry out.
    * Anti-static bag for forensic evidence
    * Faraday cage
      * Blocks communication
* This class: Evidence Acquisition
* Single-shot chance
* Considerations
  * Volatility
  * Imaging methods
  * File formats
  * Capability of imaging tools
  * Continuity in mind
  * Write-blockers
  * Image validation
  * Documenation - CoC
* Order of Volatility
  * Cache and Registers
  * ARP Cache, Routing Table, Memory, Kernel Stats, Process Table
  * Temp Files
  * Disks
  * Monitoring data and remote logging
  * Physical Configs and Network Topology
  * Archival Media
* Copy vs Image
  * A copy doesn't have metadata
  * Imaging is bit-by-bit, including slack space
* Clone vs. Image
  * Clone is physical media
  * Writes straight to the disk
  * The image cannot be used as a backup
* Acquisition tips
  * Create two images from the evidence drive in case on gets corrupted
  * The second one can be used for further analysis
* Validating
  * Hashing algorithms
  * Ensure data hasn't been corrupted or altered
* Acquisition Methods
  * Physical vs. Logical
    * Physical: Entire hard drive, all zeroes and ones
    * Logical: Takes partitions and active data, and does not include unallocated space
  * Live vs. Static
    * Live: Powered and running, or devices that cannot be turned off
      * Memory Contents, Unencrypted data, Passwords, Network Connections
      * Hard to avoid contamination
    * Static: Powered off
  * Local vs. Remote
    * Local: Physical Access
    * Remote: Network tools to create connections
