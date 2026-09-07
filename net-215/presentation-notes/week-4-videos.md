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

## RIPv2 (routing information protocol)

* Routers send out broadcasts/multicasts
* Typically sends a table every 30-60 seconds
* RIP is a Distance Vector routing protocol
  * Preference is solely based on hops
* Pro: Very easy to configure
* Con:&#x20;
  * Noisy, lot's of broadcasts, slow to covnerge
  * does not scale to large or complex networks
*

    <figure><img src="../../.gitbook/assets/image (123).png" alt="" width="375"><figcaption></figcaption></figure>



## Default Routes

* Default Route of Gateway of last resort if we don't know where to go to.
  * If destination network not found in routing table
  * Often used in home networks, sent to the ISP to be forwarded
* For routers to create a default route, we use
  * `ip route 0.0.0.0 0.0.0.0. [IP OR interface]`&#x20;
  * `ip default network [IP OR interface]`

## OSPF

* Link State Routing Protocols
  * Mst scalable method for Interior Gateway Protocol (IGP)
  * Routers figure out who their negihobrs are
  * After initial convergence, only send Hello's (keep alives) and updates with their changes
* Uses more advanced route selection metrics
  * Bandwidth
* Open Shortest Path First (OSPF)
  * Link State Advertisements
  * Send hellos every ten seconds, any changes are sent via Link State Advertisements (LSAs)
  * Essentially recursively updating.
* Example of OSPF LSA
  * LS Age: How old the change is
  * Link State ID
  * Router Advertising it
  * Network
  * and Metric

## Dynamic Routing Intro

* Routing protocols to build routing tables
* Types of Routing Protocols
  * Interior Gateway Protocols (IGP)
    * Inside an orgnaizations network
    * Contains info about internal infrastructure prefixes
    * Used IGPs:
      * RIPv2
      * OSPF
  * Exterior Gateway Protocols (EGPs)
    * Connects ISPs typically
    * Used EGPs:
      * BGP (Border Gateway Protocol)
* Why do you need an EGP?
  * IGPs don't scale well compare to EGPs.&#x20;
  * EGPs also limit networks and have additional rules and settings
  * &#x20;
