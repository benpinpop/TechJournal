# Lab 2-1: OSI Observation Capture

Objective: In this lab, students will observe traffic in a simple LAN

Goals:

* Understand the role of MAC addresses in LAN communication
* Observe ARP communication
* Introduce basic features of Wireshark and traffic analysis

#### **Perform this Lab in a Windows Virtual Machine**

**I. Observe a simple capture - Ping the Default Gateway**

1\. Capture a "ping" to the default gateway (for Ireland 017, this is 192.168.1.250; from your home network, you can use the "ipconfig /all" command to identify your gateway, or in linux use ip addr)

* On your classroom Windows VM , open a command prompt (start button and then cmd.exe)
* Type "ipconfig /all" and record the IP address of the default gateway
* Leaving the command prompt open, start the Wireshark application
* In Wireshark  **(you may need to install wireshark),** start a capture of the Ethernet interface
* Back in the command prompt, ping the Default Gateway IP address
  * ```
    ping ip_address_of_gateway
    ```
* When ping ends, go to Wireshark and stop the capture

2\. Inspect the results in Wireshark

* Click on the ICMP Ping Request packet
  * **Record:** What are the source and destination MAC addresses
    * Ethernet II, Src: 04:7c:16:0b:f3:d7. Dst: 00:00:5e:00:01:6c
    *

        <figure><img src="../../.gitbook/assets/image (109).png" alt=""><figcaption><p>Screenshot of ICMP request packet</p></figcaption></figure>
* Click on the ICMP Ping Response packet
  * **Record:** What are the source and destination MAC addresses
    * Ethernet II, Src: 4c:6d:58:1a:df:3c. Dst: 04:7c:16:0b:f3:d7
    *

        <figure><img src="../../.gitbook/assets/image (110).png" alt=""><figcaption><p>Screenshot of ICMP reply packet details</p></figcaption></figure>
* **Answer Question:** What is the MAC address of your workstation's NIC? What is the MAC address of the Default Gateway Router interface (NIC)?
  * My MAC address is: 04:7c:16:0b:f3:d7
  * The MAC for the Default Gateway is:
    * 4c:6d:58:1a:df:3c (Responder)
    * 00:00:5e:00:01:6c (Initial Destination)
    * Champlain's network is weird...

**II. Observe a simple capture - Ping outside LAN  IP addresses**

1. clear your arp cache. In an **administrator enabled** command windows type arp -d&#x20;
2. Repeat the Wireshark capture of a ping - but this time use the IP address  **34.174.229.22**
3. Inspect the results in Wireshark
   * Click on the ICMP Ping Request packet
     * **Record:** What are the source and destination MAC addresses
       *

           <figure><img src="../../.gitbook/assets/image (111).png" alt=""><figcaption><p>Screenshot of the ICMP Request Packet</p></figcaption></figure>


       * Source: (04:7c:16:0b:f3:d7). Destination: (00:00:5e:00:01:6c)
   * **Answer Question:** What is the MAC address of  34.174.229.22?&#x20;
     * You can't answer that question because the MAC addresses are replaced by the router as soon as they leave the network. Unless you have a subpoena or search warrant, good luck.&#x20;
4. Repeat the Wireshark capture of a ping - but this time use the IP address of your neighbor's workstation (someone on the same network as you)
   * **Note: the ping may fail, but capture anyway**
5. Inspect the results in Wireshark
   * Click on the ICMP Ping Request packet
     *   **Record:** What are the source and destination MAC addresses

         <figure><img src="../../.gitbook/assets/image (112).png" alt=""><figcaption><p>Screenshot of the request packet and MAC address details in Wireshark</p></figcaption></figure>



         * Src: (04:7c:16:0b:f3:d7). Dst: (78:c8:81:c8:41:dd)
   * **Answer Question:** What is the MAC address of your neighbor's PC? If the ping failed. what do you think might be the cause?
     * The MAC address of my neighbor's device (which is, in fact, a TV) is 78:c8:81:c8:41:dd. It did not fail.

**III. Review the packet headers and relate to the OSI reference model**

1. Inspect an ICMP Echo (Ping Request Packet) in Wireshark
   * The middle pane should show 4 headings
     * Frame _n_: This provides general info on the packet
     * Ethernet: This contains the decode of the bits in the Ethernet Header (Layer 2)
     * Internet Protocol Version 4: Contains the decode of the IP v4 Header (Layer 3)
     * Internet Control Message Protocol: Contains the decode of the ICMP Header
2. Answer the following questions:<br>
   * **Identify the field in the Ethernet header that indicates the next layer's header**
     *

         <figure><img src="../../.gitbook/assets/image (114).png" alt=""><figcaption><p>Screenshot of the last field in the Ethernet header indicating the next layer.</p></figcaption></figure>

         The field that indicates the next layer's header is the Type field.&#x20;
   * **Identify the field in the IPv4 header that indicates the next layer's header**
     *

         <figure><img src="../../.gitbook/assets/image (115).png" alt=""><figcaption><p>Screenshot of the last IPv4 field indiciating the next layer</p></figcaption></figure>


     * The field that indicates the next layer's header is the Destination Address field.&#x20;
   * **Look at the very first 6 bytes in the packet- what is the purpose/role of those bytes?**
     *

         <figure><img src="../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>


     * The purpose of the first six bytes is to indicate the destination MAC address of the packet.

<br>
