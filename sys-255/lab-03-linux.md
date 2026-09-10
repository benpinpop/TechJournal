# Lab 03 - Linux

## Lab

Setup Basic Rocky Linux.

{% hint style="warning" %}
Before you start, don't forget to **snapshot** and set your **network cable**.
{% endhint %}

### Step 1 - Network Setup

Use the nmtui command to navigate to the Wired Connection, and setup the following:

| **Setting**             | **Value**   |
| ----------------------- | ----------- |
| IP Address and Netmask  | 10.0.5.3/24 |
| Gateway                 | 10.0.5.2    |
| DNS                     | 10.0.5.5    |
| Search Domain           | ben.local   |
| Hostname                | dhcp01-benp |

### Step 2 - Add a privileged user

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
useradd ben # creates the account
passwd ben # sets the password
usermod -aG wheel ben # adds ben to wheel
```
{% endcode %}

### Step 3 - Add DNS A and PTR record for DHCP01

See [#dns-configuration](lab-02-ad-and-dns-setup.md#dns-configuration "mention"). The IP address is 10.0.5.3.

### Step 4 - SSH in from WKS01

Run the `ssh` command, which allows you to securely access dhcp01 remotely from your WKS01 box.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
ssh ben@dhcp01-benp
```
{% endcode %}

### Step 5 - Basic Linux Commands That I Already Know But Joe Eastman Wants Me To Write Down

| Command      | Description                                                                                          |
| ------------ | ---------------------------------------------------------------------------------------------------- |
| pwd          | Prints the working directory                                                                         |
| ls           | Lists the files in the directory. Use `ls -l` to show permissions, and `ls -a` to show hidden files. |
| cd           | Change directories                                                                                   |
| hier OR tree | Shows the hierarchy of the directory                                                                 |
| \~           | Variable for the home directory of the user                                                          |
| history      | Shows your command history!                                                                          |
| head         | Shows the top lines of an output. Use -n to specify how many lines.                                  |
| mkdir        | Create a directory                                                                                   |
| mv           | Move a file into another directory or rename a file                                                  |
| cp           | Copy a file to a new directory, or just copy a file                                                  |
| touch        | Create an empty file                                                                                 |
| nano         | Better than vi. My #fav text editor.                                                                 |

{% hint style="info" %}
See[master-linux-terminal-sheet.md](../personal/reference-essentials/linux/master-linux-terminal-sheet.md "mention") for a fuller list of commands.
{% endhint %}
