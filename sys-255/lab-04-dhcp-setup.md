# Lab 04 - DHCP Setup

## Lab

### SSH from AD01 -> DHCP 01

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
ssh champuser@dhcp01-benp
sudo -i
```
{% endcode %}

### Install DHCP and create a config file backup

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
sudo dnf install -y dhcp-server # Installs DHCP Server
cp /etc/dhcp/dhcpd.conf /etc/dhcp/dhcpd.conf.bak # Create DHCP backup file
```
{% endcode %}

### Setup Configuration

After installing the DHCP server, you need to edit the configuration.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
nano /etc/dhcp/dhcpd.conf
```
{% endcode %}

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
subnet 10.0.5.0 netmask 255.255.255.0 {
    option routers 10.0.5.2;
    option subnet-mask 255.255.255.0;
    option domain-name "ben.local";
    option domain-name-servers 10.0.5.5;
    range 10.0.5.101 10.0.5.125;
}
```
{% endcode %}

<img src="../.gitbook/assets/unknown (91).png" alt="What your configuration file should look like" height="248" width="624">

### Enable and Start DHCP & Allow Firewall

We need to enable dna start DHCP for it to actually work on our network. Use the commands below.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
systemctl enable dhcpd # Enable on startup
systemctl start dhcpd # Start the service

firewall-cmd --permanent --add-service=dhcp # Allow DHCP through the firewall
firewall-cmd --reload
firewall-cmd --list-all
```
{% endcode %}

### Change WKS01 to use DHCP

Go into the Windows Machine > Network > Network Adapter Settings > Obtain an IP address automatically.

<img src="../.gitbook/assets/unknown (92).png" alt="What the IP configuration should look like." height="569" width="472">

### Changing the Default Lease Time

Add the following into your dhcp.conf array within the brackets.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
default-lease-time 3600
max-lease-time 14400
```
{% endcode %}

## Commands and Exploration

Explore 3 other items related to DHCP, and dig into their related Wireshark captured packets

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
ipconfig /release # Releases a DHCP lease; you give up your IP address
ipconfig /renew  # Creates a new DHCP lease; you get your IP address back
```
{% endcode %}

### Types of DHCP Packets

* Release (7) - Releases your DHCP lease. You give up your IP address.
* Discover (1) - Broadcasting to the network to look for a DHCP server. 0.0.0.0 to 255.255.255.255.
* Offer (2) - DHCP server lets the device know via MAC address that it has an IP address to offer for the device.
* Request (3) - The client tells the DHCP server it is accepting the request for the IP address
* ACK (5) - The DHCP server confirms that the client has that IP address now.



<table><thead><tr><th width="99.79998779296875">Value</th><th width="219.7999267578125">Message Type</th><th width="130.7999267578125">Reference</th><th>Notes</th></tr></thead><tbody><tr><td>1</td><td>DHCPDISCOVER</td><td>[<a href="https://www.iana.org/go/rfc2132">RFC2132</a>]</td><td>Looks for a DHCP server</td></tr><tr><td>2</td><td>DHCPOFFER</td><td>[<a href="https://www.iana.org/go/rfc2132">RFC2132</a>]</td><td>DHCP server offers a an IP address</td></tr><tr><td>3</td><td>DHCPREQUEST</td><td>[<a href="https://www.iana.org/go/rfc2132">RFC2132</a>]</td><td>Client makes official request to DHCP server to confirm an offer</td></tr><tr><td>4</td><td>DHCPDECLINE</td><td>[<a href="https://www.iana.org/go/rfc2132">RFC2132</a>]</td><td>Network error packet, address might already be in use, might be more than one DHCP server</td></tr><tr><td>5</td><td>DHCPACK</td><td>[<a href="https://www.iana.org/go/rfc2132">RFC2132</a>]</td><td>Acknowledgement, final step in handshake</td></tr><tr><td>6</td><td>DHCPNAK</td><td>[<a href="https://www.iana.org/go/rfc2132">RFC2132</a>]</td><td>Opposite of an ACK, from DHCP server to Client, rejecting a request</td></tr><tr><td>7</td><td>DHCPRELEASE</td><td>[<a href="https://www.iana.org/go/rfc2132">RFC2132</a>]</td><td>Client releases the lease/IP</td></tr><tr><td>8</td><td>DHCPINFORM</td><td>[<a href="https://www.iana.org/go/rfc2132">RFC2132</a>]</td><td>Get options (configuration)</td></tr><tr><td>9</td><td>DHCPFORCERENEW</td><td>[<a href="https://www.iana.org/go/rfc3203">RFC3203</a>]</td><td>Force</td></tr></tbody></table>

Source: [https://www.iana.org/assignments/bootp-dhcp-parameters](https://www.iana.org/assignments/bootp-dhcp-parameters)

### Some DHCP Flags

* Message Type
  * 1 - Boot Request - From the client to DHCP
  * 2 - Boot Reply - From DHCP to the client
* Transaction ID - Identifies the packet conversation, starts with 0x and is 8 lowercase alphanumeric characters.
* Options
  * Carries configuration and network settings to clients
    * Packets have a list of requests; the server responds with a list of options



