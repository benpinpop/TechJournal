# Command Prompt Commands

## Basics

Use `/?`  to get command info.

### cls

Clears the terminal screen.

### ver

Displays the Windows version.

### exit

Quits the command prompt.

### echo

Prints specified arguments.

## Device Info

### hostname

Displays the computer host name. The same as using echo %COMPUTERNAME%

```powershell
C:\Users\Ben>hostname
DESKTOP-HERE
C:\Users\Ben>echo %COMPUTERNAME%
DESKTOP-HERE
```

### systeminfo

Displays system info like "operating system configuration, security information, product ID, and hardware properties (RAM, disk space, and network cards)." Can be used to retrieve info on remote and domain computers.

| /s `<computer>`          | Specifies the name or IP address of a remote computer (do not use backslashes). The default is the local computer.                                                                                                                                                                            |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /u `<domain>\<username>` | Runs the command with the account permissions of the specified user account. If **/u** is not specified, this command uses the permissions of the user who is currently logged on to the computer that is issuing the command.                                                                |
| /p `<password>`          | Specifies the password of the user account that is specified in the **/u** parameter.                                                                                                                                                                                                         |
| /fo `<format>`           | <p>Specifies the output format with one of the following values:</p><ul><li><strong>TABLE</strong> - Displays output in a table.</li><li><strong>LIST</strong> - Displays output in a list.</li><li><strong>CSV</strong> - Displays output in comma-separated values (.csv) format.</li></ul> |

[<sup>From Windows Documentation</sup>](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/systeminfo)

## Directories

### cd

Changes directories

```powershell
cd [/d] [<drive>:][<path>]
cd [..]
chdir [/d] [<drive>:][<path>]
chdir [..]

Examples:

cd .. # Changes to parent directory
cd /d C:/Users/Ben/ProgramData

# These are the same
cd Folder 
cd "Folder" 
```

### vol

Displays a disk volume label and serial number.

```powershell
VOL [drive:]

# Example
vol D:
vol C:
```

### tree

Displays all the directories of the current specified drive (unless otherwise specified).

```powershell
tree [<drive>:][<path>] [/f] [/a]

# Example:
tree c:/ /f

# Pipe to a file:
tree > file.name

# Read line by line
tree | more
```

### dir

Displays vol and list of files/folders within the directory, including dates and times when they were last modified.&#x20;

| Parameter               | Descro\[topn                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| /q                      | Displays file ownership information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| /w                      | Wide format, almost like `ls`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| /a\[\[:]`<attributes>`] | <p>Displays only the names of those directories and files with your specified attributes. If you use this parameter without specifying any <em>attributes</em>, the command displays the names of all files, including hidden and system files. The list of possible <em>attributes</em> values are:</p><ul><li><strong>d</strong> - Directories</li><li><strong>h</strong> - Hidden files</li><li><strong>s</strong> - System files</li><li><strong>r</strong> - Read-only files</li><li><strong>a</strong> - Files ready for archiving</li></ul><p>You can use any combination of these values, but don't separate your values using spaces. Optionally you can use a colon (:) separator, or you can use a hyphen (-) as a prefix to mean, "not". For example, using the <strong>-s</strong> attribute won't show the system files.</p> |
| /o\[\[:]`<sortorder>`]  | <p></p><ul><li><strong>n</strong> - Alphabetically by name</li><li><strong>e</strong> - Alphabetically by extension</li><li><strong>g</strong> - Group directories first</li><li><strong>s</strong> - By size, smallest first</li><li><strong>d</strong> - By date/time, oldest first</li><li>Use the <strong>-</strong> prefix to reverse the sort order</li></ul><p>The default sorts the directories alphabetically, followed by files.</p>                                                                                                                                                                                                                                                                                                                                                                                             |
| /t\[\[:]`<timefield>`]  | <p>Specifies which time field to display or to use for sorting. The available <em>timefield</em> values are:</p><ul><li><strong>c</strong> - Creation</li><li><strong>a</strong> - Last accessed</li><li><strong>w</strong> - Last written</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

### md OR mkdir

Creates a directory

### rd OR remdir

Removes a directory.

### del

Deletes a file or directory.

### robocopy | xcopy

Copies directories and files to the specified new directory. Use robocopy for attribute cloning, and xcopy for faster file cloning.

### move

Moves a file from one destination to another.

```
move [{/y|-y}] [<source>] [<target>]
```

### ren OR rename

Renames a file.

```
rename [<drive>:][<path>]<filename1> <filename2>
```

## Networking

### ipconfig

Ipconfig displays TCP/IP network configuration, and can refresh DNS and DHCP settings. Without parameters, it will display **IPv4** and **IPv6** addresses, **subnet mask**, and **default gateway** for all adapters.

#### ipconfig /all

Displays full configuration for all adapters. See example result below:

```
Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : champlain.edu
   Description . . . . . . . . . . . : Realtek Gaming 2.5GbE Family Controller
   Physical Address. . . . . . . . . : NUH-UH
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : 05d2:8710:ac53:6301:8fe1:8459:8bec:e7cb(Preferred)
   IPv4 Address. . . . . . . . . . . : 184.171.153.209(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Saturday, October 25, 2025 4:08:18 PM
   Lease Expires . . . . . . . . . . : Saturday, October 25, 2025 8:08:17 PM
   Default Gateway . . . . . . . . . : 184.171.153.250
   DHCP Server . . . . . . . . . . . : 216.92.151.173
   DHCPv6 IAID . . . . . . . . . . . : 1512359854
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-2A-D8-AE-7A-04-7C-16-0B-F3-D7
   DNS Servers . . . . . . . . . . . : 216.93.145.253
                                       216.93.145.247
   NetBIOS over Tcpip. . . . . . . . : Enabled
```

#### ipconfig /displaydns

Displays the DNS cache, which is used for querying commonly used websites before sending the request to the DNS server.  These records are preloaded from the local Hosts file and are commonly queried websites.

#### ipconfig /flushdns

Flushes and resets the DNS cache. Used for troubleshooting DNS issues. If a DNS query fails, a negative DNS record might be placed in the cache, stopping the computer from querying again. This means that even if the website goes back up again and the DNS record/server issue is fixed, the computer cannot access the website. By flushing the DNS, you allow your computer to query the DNS server again which might solve some issues.

#### ipconfig /release OR ipconfig /release6

Sends a DHCPRELEASE message to the DHCP for all (or specified) adapters and discards all IP configurations. Disables automatically retrieving an IP address.

#### ipconfig /renew OR ipconfig /renew6

Renews DHCP configuration for all adapters. **This only works on computers that have DHCP enabled.**

#### netstat

-n Active TCP connections

-a Ports listening to TCP or UDP

#### netcat

Lets you read and write to TCP/UDP applications.

## Net

* net user — Usernames
  * net user {username} - User Info
  * net user {username} /delete
  * net user {username} /active YES | NO
* net share — Shared Folders
* net groups

## Processes

### tasklist

Displays running applications, their PIDs, and memory amounts.

### taskkill

Terminate a specified task using either imagename or process ID.&#x20;

| /pid `<processID>` | Specifies the process ID of the process to be terminated.                                                              |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| /im `<imagename>`  | Specifies the image name of the process to be terminated. Use the wildcard character (`*`) to specify all image names. |
| /f                 | Forcefully end the task                                                                                                |
| /fi                | Filters tasks: `/fi "IMAGENAME eq "chrome*"`                                                                           |

### schtasks

List all scheduled tasks.

## Miscellaneous

### title

Sets title of CMD bar.

### set

Sets Windows environment variables

## Assorted Commands

Get-ComputerInfo OR&#x20;

more (pipe)

Add-ADGroupmember -Identity ‘GroupName’ -Members user.name

Get-ADDefaultDomainPasswordPolicy

Get-GPO -All - Get Group policy

krbtgt - Kerberos Ticketing
