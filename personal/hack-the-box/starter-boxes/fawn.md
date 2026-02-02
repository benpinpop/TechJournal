# Fawn

## Summary

HTB: Fawn is a very easy Linux machine that explores the File Transfer Protocol (FTP) and its exploitation when misconfigured to allow anonymous access.

## Questions

### What does the 3-letter acronym FTP stand for?

FTP stands for "**File Transfer Protocol**," an application used on servers to help distribute files. &#x20;

### Which port does the FTP service listen on usually?

FTP typically listens on port **21**.

### FTP sends data in the clear, without any encryption. What acronym is used for a later protocol designed to provide similar functionality to FTP but securely, as an extension of the SSH protocol?

The secure version of FTP is known as **SFTP** (Secure File Transfer Protocol).

### What is the command we can use to send an ICMP echo request to test our connection to the target?

The **ping** command can be used to test the connection.

```bash
ping insert.ip.address.here
```

### From your scans, what version is FTP running on the target?

To answer this question, we need to scan the server with nmap, a program that identifies open ports. We know ftp uses port 21, so we can narrow our scan down from there. We use the following command to identify the version:

```bash
nmap -p 21 -sV insert.ip.address.here

# -p 21 # This specifies to only scan port 21.
# -sV # This enables port service detection, allowing us to identify exactly what version of service is running on the machine
# Optional: -v # The verbose flag gives us information as the scan runs, which can be useful for larger scans. 
```

This scan gives us our result:

```
Starting Nmap 7.95 ( https://nmap.org ) at TIMESTAMP EST
Nmap scan report for insert.ip.address.here
Host is up (0.026s latency).

PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
Service Info: OS: Unix

Service detection performed. Please report any incorrect results at https://nmap.org/submit/.
Nmap done: 1 IP address (1 host up) scanned in 0.92 seconds
```

Now we know that the version is **vsftpd 3.0.3.**

### From your scans, what OS type is running on the target?

This question can be answered using our scan, which we ran a few moments ago, which is the **Unix** operating system (OS).&#x20;

### What is the command we need to run in order to display the 'ftp' client help menu?

Moving on from port scanning, this question asks us about the basics of how to use FTP. This question is not about connecting; it's just about how to display the manual/help page on your machine. To do this, we have to use the `ftp -?` command. The dash `-` signifies a command flag (an option), and the question mark `?` tells the client to display the help page. Therefore, our answer is **ftp -?**

### What is username that is used over FTP when you want to log in without having an account?

### What is the response code we get for the FTP message 'Login successful'?

### There are a couple of commands we can use to list the files and directories available on the FTP server. One is dir. What is the other that is a common way to list files on a Linux system.

### What is the command used to download the file we found on the FTP server?  <br>

\
\
<br>
