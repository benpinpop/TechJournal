# Master Linux Terminal Sheet

### Basics

```bash
echo "text" # prints stuff
cat file.txt # outputs file info

cat ~/text.txt

# Using -- ensures -testfile is treated as a filename
cat -- -testfile
# This convention is not exclusive to cat, -- signals the end of positional arguments
```

{% hint style="info" %}
A singular `/` typically designates the root directory, and can be used to separate directory names. The _tilde_, or `~` designates the home directory.&#x20;
{% endhint %}

***

### File Permissions

```bash
chmod 000 file.txt # Modifies a file

# Set file to read and write for owner, read-only for group, none for others
chmod 640 file.txt
# Breakdown:
# Owner: 6 (rw-) 
# Group: 4 (r--)
# Others: 0 (---)

# Make a script executable for everyone
chmod 755 script.sh
# Owner: 7 (rwx)
# Group: 5 (r-x)
# Others: 5 (r-x)
```

#### Permission Values

| Permission | Symbol | Numeric Value |
| ---------- | ------ | ------------- |
| Read       | r      | 4             |
| Write      | w      | 2             |
| Execute    | x      | 1             |

#### Combined Permissions&#x20;

| Numeric | Symbol | Meaning                              |
| ------- | ------ | ------------------------------------ |
| 0       | ---    | No permissions                       |
| 1       | --x    | Execute only                         |
| 2       | -w-    | Write only                           |
| 3       | -wx    | Write and execute (2 + 1)            |
| 4       | r--    | Read only                            |
| 5       | r-x    | Read and execute (4 + 1)             |
| 6       | rw-    | Read and write (4 + 2)               |
| 7       | rwx    | Read, write, and execute (4 + 2 + 1) |

***

#### Chown

Change the owner or group of a file

```bash
# Change owner to 'alice' (group stays the same)
chown alice file.txt

# Change owner to 'alice' and group to 'staff'
chown alice:staff file.txt

# Change only the group to 'staff'
chown :staff file.txt
```

***

### File Search and Display

```bash
# Display files
dir - Shows directory
pwd - Prints working directory/path
ls - Shows files and file information
```

#### ls Command

<table><thead><tr><th>Flag</th><th>Meaning</th><th data-hidden></th></tr></thead><tbody><tr><td><code>-l</code></td><td>Displays file permissions, owner, and file size</td><td></td></tr><tr><td><code>-R</code></td><td>Displays files recursively, searches through all directories</td><td></td></tr><tr><td><code>-r</code></td><td>Reverses order of search</td><td></td></tr><tr><td><code>-a</code></td><td>Shows all files, including hidden files</td><td></td></tr></tbody></table>

```bash
# Remove files
rm

# -r: Recursively
# -f: Force
```

***

### Services & Processes

#### Systemctl

```bash
# Show all active services
systemctl --type=service --state=active list-units

# Show all running services
systemctl --type=service --state=running list-units

# Show PID of process
systemctl show processName | egrep "PID" | egrep -Ev 'Control|Exec|Guess'

# Stop network manager (⚠️ NUCLEAR OPTION)
systemctl stop NetworkManager.service

# Start and stop a service
systemctl start <service>
systemctl stop <service>
```

#### Logs

<pre class="language-bash"><code class="lang-bash"><strong># Security logs
</strong>/var/log/secure

# View logs with journalctl
journalctl

# Search for failed logins
journalctl | grep "Failed"
</code></pre>

#### Process Tools

```bash
# List open files by port
lsof -i :PORT
# Example: lsof -i :443
lsof -i
```

***

### Networking

#### SS Command

```bash
ss -plunte
```

| Flag | Meaning                                 |
| ---- | --------------------------------------- |
| `-p` | Show the process using the socket       |
| `-l` | Show only listening sockets             |
| `-u` | Show UDP sockets                        |
| `-n` | Show numbers only (don’t resolve names) |
| `-t` | Show TCP sockets                        |
| `-e` | (Optional) Show extended info           |

***

#### Netstat

```bash
netstat -tuln
```

#### Open a Port

```bash
# Listen on a port
nv -lvnp PORTNUMBER
```

#### SSH

```bash
ssh username@ipaddress
```

***

### Firewall (UFW)

```bash
# Status
sudo ufw status
sudo ufw status verbose

# Deny specific IP
sudo ufw deny from 203.0.113.100

# Deny subnet
sudo ufw deny from 203.0.113.0/24

# Delete rule
sudo ufw delete allow from 203.0.113.101
```

Other options: `hosts.deny`, `hosts.allow`, or `/etc/hosts` (Rocky Linux).

***

### User Administration

<pre class="language-bash"><code class="lang-bash">passwd [USERNAME] # Changes the password, must be sudo to change other accounts
whoami # Lists the current username

useradd ## Creates a new user account # Requires sudo
adduser # Higher level of user add

<strong>usermod - Modifies a user 
</strong>usermod -aG &#x3C;group> &#x3C;username>
</code></pre>

### Hostname Administration

```bash
hostname [NEW_HOSTNAME] # Show or set system hostname
hostnamectl set-hostname [NEW_HOSTNAME] # Require sudo
```

#### Useradd common options

| Option           | Meaning                                   |
| ---------------- | ----------------------------------------- |
| `-m`             | Create a home directory for the user      |
| `-s SHELL`       | Set the default shell (e.g., `/bin/bash`) |
| `-G GROUPS`      | Add the user to additional groups         |
| `-c "COMMENT"`   | Add a description for the user            |
| `-d HOME_DIR`    | Specify the user’s home directory         |
| `-e EXPIRE_DATE` | Set expiration date (YYYY-MM-DD)          |

#### Usermod common options

| Option         | Meaning                                        |
| -------------- | ---------------------------------------------- |
| `-l NEWNAME`   | Change username                                |
| `-d /new/home` | Change home directory                          |
| `-m`           | Move files from old home to new home directory |
| `-s SHELL`     | Change the login shell                         |
| `-aG GROUP`    | Add the user to additional groups              |

### Crontab

<pre class="language-bash"><code class="lang-bash"><strong># Edit crontab for user
</strong>crontab -e

# Exit editor
:wq
</code></pre>

**Format:**

```
30 2 * * * /path/to/script.sh
```

Runs every day at **2:30 AM**.

***

### Utilities

#### Conversions & Scripts

```bash
# Download from Pastebin and convert (sudo)
curl PASTEBINID | dos2unix > script.sh && chmod +x script.sh

# Convert script to Linux format
dos2unix
```

#### Text Processing

```bash
# Extract last part of path
echo "path/to" | sed 's|.*/||'
# Example 
echo "cgroup:/system.slice/ssh.service" | sed 's|.*/||'

# Search multiple keywords
egrep "test|or|new"

# Get PID (cleaned output)
# -Ev exludes
egrep "PID" | egrep -Ev 'Control|Exec|Guess'
```

#### Loopback Addresses

```
::1   # local host (IPv6 loopback)
0.0.0.0
127.0.0.1
```

***

### Archives & Wazuh

<pre class="language-bash"><code class="lang-bash"><strong># Extracts and archives files
</strong><strong>tar
</strong># -c Create a new archive
# -x Extract an archive
# -t List the contents of an archive (without extracting)
# -f File name of the archive (must be followed by the archive file, e.g., tar -cf archive.tar files)
# -v Verbose (shows progress/details of files being processed)
# -z Use gzip compression (.tar.gz, .tgz)
# -j Use bzip2 compression (.tar.bz2)
# -J Use xz compression (.tar.xz)
#--lzma → Use LZMA compression (.tar.lzma)
# -C &#x3C;dir>
# -a Automatically picks the right compression algorithm

# Create a tarball
tar -cvf archive.tar file1 file2 dir/

<strong># Extract a tarball 
</strong><strong>tar -axf archive.tar
</strong>
<strong># Extract wazuh files and only take wazuh-install-files/wazuh-passwords.txt
</strong>sudo tar -axf wazuh-install-files.tar wazuh-install-files/wazuh-passwords.txt

# View passwords
cat wazuh-install-files/wazuh-passwords.txt
</code></pre>

### **Sorting & Uniqueness**

```bash
sort data.txt | uniq -u
# sort — ensures duplicate lines are adjacent (required for uniq to work correctly)
# uniq -u — prints only lines that appear exactly once

# To see counts:
sort data.txt | uniq -c
```

***

### **Find Command**

Using the find command with a `.` searches through the current directory. Using the find command   `/` searches through all directories.&#x20;

```bash
find / -type f -user bandit7 -group bandit6 -size 33c -print

# type: file (d for directory)
# user: bandit7
# group: bandit6
# file size: 33 bytes

# -print prints the working path, very useful for finding the exact location of a file.

# CASE SEARCHING
# Find all files ending with .txt
find . -type f -name "*.txt"

# Case-insensitive search for README files
find . -type f -iname "readme*"

#DATE MODIFIED
# Files modified exactly 7 days ago
find . -type f -mtime 7

# Files modified in the last 3 days
find . -type f -mtime -3

# Files modified more than 30 days ago
find . -type f -mtime +30

# -atime is for last accessed time
# -ctime is for last changed status
# -perm matches certain permissions

# Find files NOT owned by root
find . -type f ! -user root

# Delete all .tmp files
find . -type f -name "*.tmp" -delete

# Change permission of all .sh files
find . -type f -name "*.sh" -exec chmod +x {} \;
# {} is replaced with the filename, \; ends the command.
```

### Release Info

cat /etc/os-release

hostnamectl

uname -r (Linux Kernel in use)

uname -a (More comprehensive information

cat /proc/version (Kernel version and build info)

### Vim

Use vi to open vim. Press Esc + i to edit. Press Esc + :wq to save

Or :q! to exit without saving&#x20;

Navigation: h (left), j (down), k (up), l (right). You can also use numbers before a command, like 5j to move down five lines.



### Awk

Awk allows you to split and filter strings.

```bash
# awk 'pattern { action }' file

# prints every line
awk '{ print }' data.txt

# Splits using the ":" 
echo "string:test" | awk -F: '{print $2}' 

# Prints
awk '{print $1, $3}' data.txt


```

#### Size options

|  Suffix | Unit            | Meaning             | Example     | Description                  |
| :-----: | --------------- | ------------------- | ----------- | ---------------------------- |
| **`c`** | bytes           | 1 byte              | `-size 33c` | File is exactly 33 bytes     |
| **`k`** | kilobytes       | 1024 bytes          | `-size 2k`  | File is exactly 2 KB         |
| **`M`** | megabytes       | 1,048,576 bytes     | `-size 5M`  | File is 5 MB                 |
| **`G`** | gigabytes       | 1,073,741,824 bytes | `-size 1G`  | File is 1 GB                 |
| **`b`** | 512-byte blocks | —                   | `-size 2b`  | File is 1024 bytes (2 × 512) |

#### Greather than/Less than

|  Prefix  | Meaning          | Example       | Description                   |
| :------: | ---------------- | ------------- | ----------------------------- |
|  **`+`** | Greater than     | `-size +10M`  | Files **larger than 10 MB**   |
|  **`-`** | Less than        | `-size -100k` | Files **smaller than 100 KB** |
| _(none)_ | Exactly equal to | `-size 33c`   | Files **exactly 33 bytes**    |

### Removing Errors

```bash
2>/dev/null
```

## Digital Forensics

### Important directories:&#x20;

1. `/etc`&#x20;
2. `/var/log`
3. &#x20;`/var/log/`&#x20;
4. `/var/www`&#x20;
5. `/root`&#x20;

### Log Files

{% columns %}
{% column width="50%" %}
/var/log/auth.log

/var/log/syslog **or** systemlog

\~/.bash\_history
{% endcolumn %}

{% column width="50%" %}
/var/log/access.log **(Apache Only)**

journalctl command


{% endcolumn %}
{% endcolumns %}

### Persistence Mechanisms

#### Services&#x20;

Check running services using systemctl. Identify any services out of the ordinary.

#### Cronjob

&#x20;Scheduled Tasks, but for linux. Check `/var/log/syslog` (Debian/Ubuntu) for cron logs. If you have access to `journalctl`, use the command:

```
journalctl -u cron.service
```

#### SSH with Priveleged Users

Identify users with sudo access who could SSH in. Check all user accounts in `/etc/passwd` .&#x20;

{% hint style="info" %}
To extract all usernames, use the awk command.

```
awk -F: '{ print $1 }' /etc/passwd
```
{% endhint %}
