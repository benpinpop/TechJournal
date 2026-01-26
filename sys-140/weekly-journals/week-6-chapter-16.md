# Week 6: Chapter 16

## Notes

### System Utilities

A system utility is an application that allows you to perform a variety of maintenance tasks on your computer, from viewing and modifying files, cleaning up disks, virus scanning, to defragmenting your discs.&#x20;

<br>

A file manager allows you to view and edit your files. Each operating system has its own file manager, but you can download others. Organize your files with folders, rename or add files, file managers do all things files.

<br>

A search utility is a program that allows you to search through the internet or your files, displaying information about the results. On Windows, that would be the Search bar on the bottom left.&#x20;

<br>

An image viewer, slightly self-explanatory, allows you to view, copy, print, or modify images, something like 3D Paint or Photos in Windows.&#x20;

<br>

A disk cleanup program allows you to clean up your disks and remove unneeded files like temporary or downloadable files that are being unused.&#x20;

<br>

An uninstaller removes any instances of a downloaded application. This is typically available through your Operating System. In Windows, this might come as a Control Panel. Some applications may not register themselves with the operating system, requiring you to manually delete them. Typically, most well-known applications come with uninstallers.

<br>

A disk defragmenter defragments your drive so that it can operate and run faster. When storing files, the disk places them in the first open spot. Over time, this results in fragmentation, slowing down file access. Defragmenting your disk often is key to ensuring your disk runs smoothly. Most operating systems will come with disk defragmenters.

<br>

A backup and restore utility allows you to copy your files and operating system information to a USB Drive or other storage device. Typically, these files are compressed to save space. The restore utility decompresses these files and allows you to restore your system from your backup in the event of system failure or file corruption.

<br>

Screen savers are images (optionally moving), activated after a designated period of inactivity on your computer. Originally designed to stop screen burns, they are more popular for their security benefits. Many computers require passwords to be re-entered after the screen saver is enabled to stop potential attackers from accessing your computer. If you left your computer alone, someone might be able to access your files if not for a screen saver.

A personal firewall monitors all network traffic going in and out of your computer. With this utility, you can set rules and filters for traffic to stop unwanted requests from coming to your computer. Most modern operating systems come with a firewall.

<br>

Antivirus programs proactively scan your computer for potential threats and stop malware from being downloaded on your computer. Some antivirus programs are better than others. (Enough said.)

<br>

A file compression utility compresses files to a smaller size. File compression is extremely useful, allowing you to save space and bandwidth over the internet while sharing or storing files. Compressed files are typically much smaller than the original size, but they require being unzipped before being viewed. File compression utilities will have file decompression utilities as well, allowing you to view these compressed files with ease. (It sometimes takes a lot of time to unzip big files!) You may see the file extension .zip or .7zip commonly used.

<br>

A media player allows you to play any form of audio or video, but may include a way to acquire, edit, or convert media files.&#x20;

### Textbook

#### Computer Management Console

The Computer Management Console is a “snap-in” (modular), allowing you to access a variety of technical tools to work on your computer. You can open this console with compmgmt in the Run tool. The Computer Management Console gives you a comprehensive view of the system, shared files, services, and other information to help you diagnose any issues or problems. The three main categories you’ll see are Tools, Storage, and Services and Applications.

**System Tools**&#x20;

A category of the CMC is System Tools, including Task Scheduler, Event Viewer, Shared Folders, Users and Groups, Performance, and Device Manager.

<br>

The Task Scheduler is the equivalent of Cron Jobs for Linux on Windows. You can set certain automated or triggered tasks in the task scheduler. The Event Viewer is the event log for Windows, allowing you to see when certain tasks fail or succeed, or when drivers are set up, etc. There are windows and application/service logs. Each log entry comes with log categories and success types.&#x20;

<br>

Logs from Windows originate from Application, Security, Setup, and System. A lowercase “i” is an information log. A ! or X means a warning or error, and a yellow key or lock indicates an audit success or failure.&#x20;

<br>

Applications can designate what events they want displayed in the Event Viewer. Security logs typically include login information and are only viewable by Administrator accounts. The most commonly used logs are the system logs, which are uneditable and undeletable.

<br>

The Shared Folders tool allows you to view folder shares, user sessions and the files opened by users. Shares are folders that have been shared on the network. Sessions are the users currently logged in on the network.

**User Account Management**

The User Account Management category allows you to create and manage accounts as well as view and edit credential keys. You can view credentials from the website and Windows credentials in the Credential Manager.&#x20;

<br>

You can also view local users and groups (lusrmgr.msc) and edit these accounts. Local Users are managed by the computer, whereas domain/global users are managed by network administrators. Each account is assigned certain permissions and rights. Permissions allow you to view certain files. Rights allow you to execute certain computer actions. For example, some users may be denied certain rights, like executing PowerShell scripts for security reasons or downloading files.

<br>

There are two types of accounts: Standard and Administrator. The administrator has full access, whereas a standard user has limited permissions.  In Windows Pro, there are additional levels of user accounts, specifically the power user.

#### Managing Services And Applications

You can manage your services and applications through the services panel (or through the computer management system). By double-clicking on a service, you can view its properties and additional information. By right-clicking on a service entry, you can start, stop, pause, or resume tasks. You can set how a service recovers after failure in the properties tab, restarting, or notifying a technician.

#### Overview of the Windows Boot Process

When booting a system, the BIOS looks for an operating system on a variety of storage devices connected to it. You can choose to change which device it looks for first to boot up a different operating system. The BIOS looks for a hard drive, then an optical drive, an external hard drive, like USB Drive, a network drive, and an internet image. You can set this boot order in the BIOS.

<br>

The system volume has the files that load the operating system, and the boot volume is where the actual operating system files exist. These can exist on the same partition as each other.

<br>

When booting up, Windows takes the following steps:

<br>

* Preboot: Looks for an operating system and allows for it to load
* Windows Boot Manager (bootmgr.exe): WBM executes, and locates winload.exe to load Windows
* Windows operating system loader (winload.exe): Select drivers are loaded
* Windows OS kernel (ntoskrnl.exe): Final operations complete and the login screen shows up

<br>

The windows installation typically has all the drivers you need.

<br>

![](<../../.gitbook/assets/unknown (31).png>)

<br>

The system root typically is C:/Windows, whereas the %systemdrive% would be C:/. This also depends on whether the drive is partitioned.&#x20;

<br>

![](<../../.gitbook/assets/unknown (32).png>) (this is funny)

<br>

To solve system boot issues, you can use the Boot Recovery application (bootrec).

<br>

#### Recovery Console

The Recovery Console is a screen that displays when the system crashes (Blue Screen of Death, anyone?) or has other boot issues. It provides a variety of options to troubleshoot, allowing you to use another boot device, go into the command prompt, go into your BIOS, etc. You can also press continue if you want to attempt to default boot into your operating system. All of these tools are stored in a different partition that is designated for recovery. To open Windows Recovery, you can use the following commands:\
\
reagentc /boottore OR shutdown /r /o

#### Advanced Boot Options/Startup Settings Menu

If you want yet another boot utility, you can use the advanced boot options menu by restarting in the Windows Recovery Console. It comes with even more options from booting in Safe Mode, Safe Mode with Networking or Command Prompt, Boot Logging, Debugging Mode, Disabling Driver Signature Enforcement (that sounds like a horrible idea), disabling the anti-malware (that sounds like an EVEN WORSE IDEA), and of course, starting Windows normally.&#x20;

#### System Configuration Utility

<br>

The system configuration utility allows you to troubleshoot boot issues by setting which boot mode you’d like to use. There are three types: normal, diagnostic, and selective. Normal loads all drivers like usual, diagnostic boots into Safe Mode, which has only the most basic drivers, and diagnostic allows you to select which drivers you want to load. This only refers to services and drivers that run on startup.&#x20;

<br>

The boot tab on top allows you to select a variety of options on top of the basic three boot types.&#x20;

<br>

![](<../../.gitbook/assets/unknown (33).png>)

<br>

Minimal boots you into Safe Mode without networking, only the most critical of system services. The alternate shell boots you into the command prompt. Network boots you into Safe Mode with Networking enabled. No GUI boot has no welcome screen; boot log creates a text file with all the boot information (ntbtlog.txt). Base Video is low-resolution, and OS boot information will display all the driver information as it boots up. The timeout is just how long the system will wait before it reverts back to default settings.&#x20;

<br>

In the services tab, you can select which services you want to disable. You can hide all Microsoft services to see what services are installed by other applications.

<br>

The Startup tab will open the Task Manager to its Startup tab.

<br>

The tools tab has a list of basic tools used for troubleshooting that you can open up, much like the Computer Management Console.&#x20;

<br>

![](<../../.gitbook/assets/unknown (34).png>)

#### Task Manager

Task Manager is a Windows utility that provides information about running applications, allowing you to view and kill tasks. The Processes tab provides a list of information about running tasks, displaying task component utilization like CPU, RAM, Disk, and GPU usage. The performance tab displays total component usage for the CPU, RAM, Disk, GPU, Network, and other attached devices. The App History tab provides information about the history of any running applications, specifically network usage and how much CPU time they’re using. The Startup Application tab is used to enable or disable applications that start on boot/login. The Users tab gives you access to disconnect logged-in users. The details page provides a little more information on running processes, though it’s not guaranteed that entries on the details page are in the processes tab. The details page contains the PID of applications, which is helpful.&#x20;

<br>

## Guiding Questions (Answer 2)

Pick one of these tools available in the System Management console (Task Scheduler, Event Viewer, Shared Folders). Do you think you would find it useful when doing your day-to-day computing tasks? Why or why not?

<br>

Eh, not really. For the most part, I typically use Task Manager if I find annoying tasks, and that’s enough for me. If I ever have an issue with a service or application that I really can’t remove by deleting its files, I could possibly go to Task Scheduler and get rid of it there, but for the most part, using an uninstaller works just fine. On the other hand, I could probably test it out on my laptop that has like 10 instances of Recall running, which I would love to disable. Otherwise, Task Manager and File Explorer work perfectly fine for my needs, and I have no issues.

<br>

Have you ever had to use the Recovery Console to boot your computer? If so, discuss your experience with the tool: Was it easy to use? Were you able to solve the problem?

<br>

Yes, I have used the Recovery Console before when I’ve lost power and my Windows shut down improperly. For the most part, I’ve either restarted or just booted back into my system by pressing continue. My system has never been bricked in a way where I need to troubleshoot any more than that, and I’ve had no issues, thank god. So yes, it was extremely easy to use, but I don’t touch the advanced options unless I have to because I know that I might mess up my computer even more.&#x20;

\
<br>
