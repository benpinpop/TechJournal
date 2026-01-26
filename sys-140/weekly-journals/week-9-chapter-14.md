# Week 9: Chapter 14

## Notes

### Networking Overview

A network allows two computers to communicate and share resources, like communicating through the internet, utilizing printers or scanners, or sending and receiving emails. There are multiple classifications of networks.

<br>

A personal area network (PAN) is almost like IoT devices, which are all connected to each other, like a phone and earbuds. These could be wired or wireless. Bluetooth is the most common use of a personal area network, running in the 2.4 GHz range. Bluetooth has three levels/ranges of connectivity, with a max speed of 24 Mbps. Slower speeds (2 Mbps) are offered for higher ranges up to 800 feet (holy moly), known as Bluetooth Low Energy (BLE). PANs are typically limited to eight devices. Bluetooth devices also encrypt their data with 128-bit encryption.

<br>

A local area network (LAN) is a group of devices on a single network (typically Ethernet), like computers in a classroom. For example, cyber.local would be a LAN. A hub or a switch centrally connects LANs (Ethernet connects through RJ45). A hub does not examine the data coming through it, whereas a switch does. Data collisions due to delay (race condition, much?) can be stopped by switches, as they can examine the data coming through the network.&#x20;

<br>

Switches can be managed and given IP addresses, or they can just connect other computers through a network. (Kind of like a router). If a cable fails, the network still stays up. Ethernet can support speeds up to 100 Gbps. (You do not need these kinds of speeds.)

![](<../../.gitbook/assets/unknown (46).png>)

<br>

LANs are either work groups or domains. Work groups are small, usually have one network, and are much easier to implement. Domains are centrally managed by the network, much larger (20+), with centralized storage and user accounts. See an image below for domain networks.

![](<../../.gitbook/assets/unknown (47).png>)

<br>

When you’re connected to a wired LAN, you are either on a workgroup, domain, private, or public network. Workgroups are typically for homes and small businesses for increased efficiency. Domain networks are for enterprise users. Private networks are for home networks, and public networks are for networks in which you don’t know the other devices.&#x20;

<br>

&#x20;A WLAN, or Wireless LAN, connects devices across buildings or through the area. Consider a modem and a router (without an Ethernet cable, of course), which would be a WLAN. These use radio frequencies and are typically used in home networks or other networks, particularly WiFi.

<br>

A Metropolitan Area Network (MAN) connects multiple networks together. A little larger in scale is Wide Area Networks, which are farther apart than MANs. WANs can be Wireless, using long-range cell towers.\
\
Wireless Mesh Networks are built by peer devices, rather than a singular distributor like a modem or router, so the network is resistant to going down. Like peer-to-peer radios, for example.

<br>

A storage area network isn’t really a network, but rather a collection of storage devices that are available to or through the network. Imagine a computer, but with the storage just outside the system in its own system.&#x20;

![](<../../.gitbook/assets/unknown (48).png>)

<br>

### Network Topologies

No entry in the textbook for this.

### The OSI Model

The OSI (Open Systems Interconnect) model sets standard guidelines for how networks transfer data to each other. Networks are split into 7 layers, shown below.

![](<../../.gitbook/assets/unknown (49).png>)

<br>

Each layer provides more functions to the data being transported. To access data from a certain layer, you have to access the layers below. So to access the transport layer, you need to access the network layer, which goes through the data link and physical layer.&#x20;

<br>

From the top down, data is given a header from each layer. When receiving data, each layer from down up removes a header (for processing). Data from each layer is given a name. At the physical layer, it's bits, at the network layer it's a frame, and at the network layer it's a packet.

![](<../../.gitbook/assets/unknown (50).png>)

Each layer has a purpose. The bottom three layers process data, and the rest handle distributing that data.&#x20;

<br>

Physical layer handles the bits, the physical data that is being transferred. The data link layer handles error control (MAC addresses) and changes the bits into frames. Network sorts the data and sends it on its way. Transport provides a mechanism for data sending, session handles the synchronization and communication, presentation translates the data, and application gives network services. For example, the firewall runs at the application layer.

### The TCP/IP Model

A network protocol is a protocol for how networks communicate. A protocol suite is defined as a “group of protocols that are designed to work together.” The TCP/IP (Transmission Control Protocol/Internet Protocol) is a protocol suite that encompasses a large number of modern internet protocols that we use today, like TCP, IP, DHCP, FTP, and HTTP. There are only four layers in the TCP/IP model: Application, Transport, Internet, and Network Access.

![](<../../.gitbook/assets/unknown (51).png>)

The Network Access layer tells you how to format data, using MAC addresses. The internet layer translates the MAC address into an IP address, the transport layer adds port numbers (so the computer knows which application to send it to), and the application layer handles all the processing of that information.&#x20;

<br>

Hubs and cables run at the physical layer, switches and wireless access points function at the data link layer, and routers run at the network layer.&#x20;

### Network Addressing

There are two different addresses associated with computers and how they communicate. A MAC address is a 48-bit unique hexadecimal number that is burned onto every chip, with the first half designating the manufacturer, and the second half being a unique identifier for the computer. A MAC address is considered a layer 2 or physical address. They can be formatted in a variety of ways, either with dashes or colons (00-11-11-71-41-10 OR 01:11:11:71:41:10).&#x20;

<br>

An IP address is a much more dynamic number associated with a computer, and is how you communicate with most computers or devices. IPs are assigned when you connect to a network, and are part of layer 3. There are two versions, IPv4 and IPv6. An IP address is also unique, but it can change. IPv4 addresses are 32-bit numbers in dotted decimal notation. IPv6 addresses are 128 bits in hexadecimal notation (fe80::13e:4586:5807:95f7). IPv6 addresses with double colons mean a zero has been omitted from the octet. You can only have one double colon in an IPv6 address. (Why?)

<br>

IPv6 addresses are local, so they cannot be used to communicate outside your network. IPv4 is a little different, with five classes from A to E. A to C are for network devices, D is for multicasting, and E is for experimentation (huh).&#x20;

\
<br>

| Class | First octet (number) of the IP address |
| ----- | -------------------------------------- |
| A     | 0 to 127                               |
| B     | 128 to 191                             |
| C     | 192 to 223                             |

<br>

IPs are also separated into private and public IPs. Private addresses can only be spoken to inside the network, and public IPs can receive traffic from outside the network.&#x20;

<br>

Private addresses are as follows (from the textbook):

| A | 10.x.x.x (where the x represents any number from 0 to 255), or 10.0.0.0 through 10.255.255.255 |
| - | ---------------------------------------------------------------------------------------------- |
| B | 172.16.x.x through 172.31.x.x, or 172.16.0.0 through 172.31.255.255                            |
| C | 192.168.x.x, or 192.168.0.0 through 192.168.255.255                                            |

<br>

### More IPv4 Addressing

There are two parts to an IP address: a network number (designating the network), and the host address (designating which computer, which is unique). Depending on the class of network, the network and host address numbers are assigned a certain number of bits. For example, in the most common home Class C networks, you have 24 bits assigned to the network address, with 8 left for the host. It’s the opposite for class A addresses. This means for class A, that you can have more devices connected (224 or 16,777,214 hosts).

![](<../../.gitbook/assets/unknown (52).png>)

<br>

Almost every single network uses a private IP address for internal networking.

<br>

No IP address can have a zero as the last octet, because that is taken by the network itself, or 255, because that is the broadcast address to send info to all devices on the network. (I did not know this.)&#x20;

#### VLAN (Virtual Local Area Network)

VLANs are a way of creating multiple networks through a switch. For example, if you have multiple devices that you want on separate networks, like phones, computers, and printers. Each would be assigned a different network address so that they are fully separate. Not all switches support VLANs, but if they do, “all ports are assigned to VLAN 1 by default.” VLANs allow you to increase security and reduce broadcast overhead.&#x20;

#### Subnet Masks

On top of an IP address, you need a subnet mask, which tells the computer what class of IP address, or what portion represents the network address and the host. For example, a Class A IP address is 255.0.0.0, meaning that the rest of the octets are given to the hosts. (THAT MAKES SO MUCH SENSE HOLY MOLY). Subnet masks can be represented by 1s and 0s (11111111.00000000.00000000.000000000), referring to the binary bit values. Class A would be /8, B is /16, and C is /24.

<br>

Sometimes you’ll see an IP address with a slash at the end with numbers (192.168.1.0/24). This is called a classless inter-domain routing (CIDR) address or CIDR subnet mask. The slash indicates how many zeroes are assigned to the network address, and how many zeroes (or bits) are left for the host address. Because there are always 32 bits in an IPv4 address, you can always just calculate by subtracting the number from 32 to tell how many bits are left.

### Network Troubleshooting

There are multiple ways to check if you are connected to the internet and troubleshoot network issues. Use ping to ping certain IP addresses to see if you receive a response. For example, if you can’t access a file on a server, try pinging it to see if you’re even connected. If you’re getting only a few responses back, it could be an issue with port flapping (ports opening and closing).&#x20;

<br>

The first sign of a network issue is someone being unable to access resources, so using ping is extremely helpful. You can use ping -t to ping continuously.&#x20;

<br>

If you have an issue with a website and you can ping its IP address, then it’s an issue with the DNS server. If you can’t ping your localhost, you have a TCP/IP issue.&#x20;

\
Ipconfig is an extremely useful command to tell you what networks you are attached to and what your IP configuration is. (ipconfig /all). If you are having an issue with receiving an IP address, run the ipconfig /release and ipconfig /renew, as it is likely a DHCP issue.&#x20;

<br>

You can also use tracert to see how packets travel over a network and identify what is causing a bottleneck.&#x20;

<br>

Pathping combines ping and tracert to provide more information, but also takes longer than both of the commands.

\
Nslookup helps you troubleshoot DNS servers and will give you the IP address of a website. To clear a DNS cache, use ipconfig /flushdns.

<br>

The net command is an extremely helpful command to manage everything network-related from your computer. (I’ve used this before with net user, net accounts, for AD)

\
<br>

net \[ accounts | computer | config | continue | file | group

\| help | helpmsg | localgroup | name | pause | print | send |

session | share | start | statistics | stop | time | use |user | view ]

<br>

The netdom command handles domain environments, allowing you to add and join domains.

## Guiding Questions (answer 3):

* How would you classify Champlain's network (for example, is it a PAN, LAN, or WAN)? Justify your answer.
* I would say that Champlain’s network is a WAN because you can connect devices over WiFi. While some devices, like cyber.local are LANs because they are internal networks, all of our devices can be connected wirelessly, making them different from LANs. You can still connect with an Ethernet cable, nonetheless.
* Between the OSI and TCP/IP models, which one seems more useful for describing networks? Justify your answer.
* I think the OSI model is extremely useful for breaking down networks technically, but it is hard to understand for the average person, and some layers are confusing in terms of how they work. The TCP/IP model is much simpler, providing only three layers: network access, internet, and application. While this makes the most sense for the average person, it still leaves out crucial and critical details on how networks actually function. It properly explains the usage of MAC and IP addresses, but fails to mention the complicated details of how networks actually process the data that is being transferred. Both models are extremely useful, but if I had to choose, I would pick the OSI model.&#x20;
* Suppose Champlain College was given a Class A network ID for its network (i.e., it had 224 addresses to assign to computers).  Give one reason why this would be a good thing, and one reason why this might be a bad thing.
* One reason it might be a good thing is that it could handle a large number of host devices, supporting thousands of students. The issue with that is running maintenance and monitoring on these addresses would suck, because there are quite literally 224 addresses. Scanning 255 (Class C) addresses and all their ports for vulnerabilities is long enough, but it would take quite literally forever to check all the addresses on a Class A network ID. In addition, the amount of infrastructure, RAM, and processing required would likely be extremely expensive in comparison to the benefit that the capacity would provide. Not only does Champlain not have that many devices, but it does not need that much capacity. If anything, it’d be much cheaper to have a Class B network ID, and you’d have the capacity for 216 addresses, or 65 thousand devices.&#x20;

<br>

<br>
