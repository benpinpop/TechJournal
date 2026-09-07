# Week 4 Videos

## IP

* Layer 3 Protocol
* What does it do?
  * Addressing
    * Identifies a network address as well as a unique host address of a device interface.
  * Routing/Indirect Delivery
    * Routers route the packets using the addressing scheme
  * Fragmentation and Reassembly
    * Layers 1 & 2 have max sizes, so IP breaks it up into pieces (Fragmentation)
    * The device uses reassembly to create the whole IP datagram
* IP header
  *

      <figure><img src="../../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>


  * IP flags
    * Evil bit - IDS
  * Time to Live Field
    * Once it runs out to 0, the packet is dropped.&#x20;
    * 255 is the max, decrease by one for every router.
    * 64 and 128 are the most common values.

## ICMP Intro

* Internet Control Messaging Protocol
* Health and maintenance protocol, carries system messages
  * Ping uses ICMP
* Two message types
  * Reporting errors
  * Obtaining information
* Echo Request and Echo Reply
  * Ping!!!
* Errors
  * Time Exceeded and Destination Unreachable
    * Unreachable if no route xists
  * Datagram tiems out if TTL count expires
*

    <figure><img src="../../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>


* Type field
  *

      <figure><img src="../../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>


  * Mostly 8s and 0s.

## Intro to Static Routing

* Routes things! Routers are layer 3, and switches are layer 2, and hubs are layer 1.
* Makes decisions based on IP address information.

## Routing Tables

* Determiens where to send the next packet, routers consult routing tables!
* Contains:
  * Network Address
  * Subnet Mask
  * Next Hop
  * Interface
* May also have
  * Distance
  * Preference (More than one route, which one is better?)
* It doesn't need to know the path, just the next router.
* Switching Tables - CAN tables
  * MAC addresses, rather than IP addresses
  * MAC addresses and ports
* Routing Tables
  * Network IDs and the IP of the next router in that direction
* Direct vs. Next Hop

## RIPv2

