# Windows Logs Night

## SRUM

* SRUM: System Resource Usage Monitor
* A database: Windows 8 and Server 2012
* Tracks stuff to diagnose issues: It's a task manager
* SRUM is the backend of task manager
* Uses
  * Timeline reconstruction
  * Application usage
  * Resource consumption
  * network usage
* Tables
  * App resource usage
    * App path and ID
    * User ID
    * Date and Time
  * Energy Usage & Energy Usage Long Term
    * AC and DC / shows wall power
  * Network connections
    * Interface type
    * Connection length
  * Network usage
    * Bytes sent and received
    * App ID
  * Push Notification
    * Path to app
* Path: C\Windows\System32\sru,
  * C:\Windows\System32\confg
  * SrumECMD
  * esentutl /r sru /i'

## Sysmon

* System Monitor
  * It's a part of Sysinternals
  * An extension of event logs
  * 30 unique events
  * **Needs to be downloaded**
* Important event IDs
  * 1 Process creation
  * 3 Network connections
  * 5 Process terminated
  * 11 File created
  * 13 Registry value set
  * 23 File deleted
* Extract
  * Use FTK
