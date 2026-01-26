# Reconnaissance

## Nmap

Nmap is used for port and operating system discovery. Nmap requires a target domain or IP address to scan.&#x20;

To scan a target, use the the following command:

```
nmap domainname.com
```

### Scan Options

#### List Scan (-sL)

While you can use this for an individual address, I typically recommend using a list scan for a CIDR address. The list scan lists all the hosts it is going to scan, and performs reverse DNS resolution (IP --> domain name). See an example code block below.

```
C:\Users\benpo>nmap -sL 192.168.1.1/24
Starting Nmap 7.97 ( https://nmap.org ) at TIMESTAMP HERE
Nmap scan report for 192.168.1.0
Nmap scan report for gateway.router.home (192.168.1.1)
Nmap scan report for service3.router.home (192.168.1.2)
Nmap scan report for service1.router.home (192.168.1.3)
Nmap scan report for randomdomainnamehere (192.168.1.4)
Nmap scan report for 192.168.1.5
Nmap scan report for 192.168.1.6
...
```

{% hint style="warning" %}
The list scan does not actually ping any hosts, so it is not considered a real scan. Rather, it just performs reverse DNS resolution to learn the names of the hosts.
{% endhint %}

#### Ping Scan (-sn)

A ping scan is much like a list scan, but instead pings the hosts. This shows whether the hosts are **online**, the **MAC Address** of the host, and the **domain name** (if available).

```
C:\Users\benpo>nmap -sn 192.168.1.4
Host is up (0.012s latency).
MAC Address: EC:F4:BB:AA:AA:AA (Dell)
Nmap scan report for wireguard.fios-router.home (192.168.1.4)
```

{% hint style="info" %}
This scan does not scan any ports.
{% endhint %}

### Options List

```
Usage: nmap [Scan Type(s)] [Options] {target specification}

TARGET SPECIFICATION:
  Can pass hostnames, IP addresses, networks, etc.
  Ex: scanme.nmap.org, microsoft.com/24, 192.168.0.1; 10.0.0-255.1-254
  -iL <inputfilename>: Input from list of hosts/networks
  -iR <num hosts>: Choose random targets
  --exclude <host1[,host2][,host3],...>: Exclude hosts/networks
  --excludefile <exclude_file>: Exclude list from file
HOST DISCOVERY:
 -sL: List scan, does not send any packets, does reverse DNS resolution to learn names of the hosts.
   Prints a list of target hosts, not a real scan.
 -sn: Ping Scan, disables port scanning, much faster
 -Pn: Treats all hosts as online
```

## Gobuster/Ffuf

[Gobuster](https://github.com/OJ/gobuster) and [Ffuf](https://github.com/ffuf/ffuf) are used for subdirectory fuzzing.

### Gobuster Examples

```bash
gobuster dir -u https://example.com/ -w wordlist.txt
```

### Ffuf Examples

```bash
ffuf -w wordlist.txt -u http://website.com/FUZZ'

-fc # Use -fc to filter response codes
```

## Recon-ng

Using `shell` will output any commands to the terminal. The `help` command lists all commands with their description.&#x20;

{% hint style="info" %}
Use `Tab` to autocomplete or list commands.&#x20;
{% endhint %}

### Marketplace

Marketplace allows you to install modules to perform recon. Any module marked with a `D` has dependencies, and any marked with a `K` requires API keys.

<pre class="language-bash"><code class="lang-bash">Usage: marketplace &#x3C;info|install|refresh|remove|search> [...]

# Self-explanatory
marketplace remove moduleName
marketplace install moduleName

# Lists all modules
marketplace search

# Refresh the marketplace
marketplace refresh

# Provides module info
<strong>marketplace info recon/hosts-ports/shodan_ip
</strong></code></pre>

### Workspaces

Workspaces allow you to containerize your testing environments, so that you can generate reports for individual targets.&#x20;

```bash
Usage: workspaces <create|list|load|remove> [...]

workspaces create workspaceName # Create a new Workspace
workspaces list # List all workspaces
workspaces load workspaceName # Load a workspace
workspaces remove workspaceName # Remove a workspace
```

### Modules

The `modules` command allows you to interact with the currently installed modules.&#x20;

```bash
Usage: modules <load|reload|search> [...]

# Example of loading a module
modules load recon/domains-contacts/whois_pocs

# After using a module to return to the workspace
back

# Example of a search
modules search ports
```

{% hint style="info" %}
Use the `info` command once you've loaded a module to get more info about it.
{% endhint %}

### Options

The `options` command allows you to set module options before running it. This may be a required step, like setting a module target before you run it.

```bash
Usage: options <list|set|unset> [...]

# Unset the current target source
options unset SOURCE

# Set the current target source
options set google.com

# List all options
options list
```

### Database (db)

The db command creates a database for the workspace.

```bash
Usage: db <delete|insert|notes|query|schema> [...]
```

### Show

The show command displays report information from the database.

```bash
Usage: show <companies|contacts|credentials|domains|hosts|leaks|locations|netblocks|ports|profiles|pushpins|repositories|vulnerabilities>
```

### API Keys (keys)

Manages your API keys for modules that need them.

```bash
Usage: keys <add|list|remove> [...]

keys list

keys add
keys remove
```

### Module Documentation

## Hackerone Notes

### Extracting Targets from a CSV file

```bash
awk -F, '{print $1}' targets.csv
```

### Extracting IP addresses

```bash
grep -oE "([0-9]{1,3}\.){3}[0-9]{1,3}" your_file.txt > ips.txt
```

