# Lab 3-1: ARP Observation

## Writeup

In this lab, we did a simulation of ARP requests, modeling how ARP broadcasts and replies work on our local network. I used my own Proxmox home lab and used one pre-made Kali VM, and an empty Debian 13 VM assigned to the same subnet (192.168.2.1/24).&#x20;

Any commands or instructions that you found useful and will need to use again in the future.

* _arp -d \[hostName OR ipAddress]: Deletes ARP Cache entry_
* _arp: Displays the ARP Cache_
* _Use arp as a filter in wireshark_

Any problems you ran into during the lab, and what troubleshooting steps you took to fix them.

* N/A

## Deliverables

1. Analyze Capture for ARP packets:
   * **Deliverable 1: Find the ARP broadcast that your computer used to find the gateway's MAC address. Provide a screenshot that shows the source and destination MAC address of this broadcast.**
     *

         <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
     * In this screenshot, you can see the ARP requests made to the gateway from the Kali Machine. If you look at the bottom left, you can identify the sender MAC address, bc:24:11:e3:b3:cd, and the target MAC address, 00:00:00\_00:00:00. The target MAC address is empty because the device does not know the MAC address and is trying to identify it via ARP.&#x20;
   * **Deliverable 2: Find the ARP reply from the gateway back to your computer. Provide a screenshot that shows the ARP reply packet indicating the MAC address for your gateway.**
     *

         <figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
     * This screenshot shows the ARP reply made from the gateway to the computer. ARP is a Layer 2 protocol, meaning the Source is the MAC Address, not the IP Address. The Source MAC Address is 42:15:a0:09:3a:ce, which can be found by looking at the "Sender Mac Address" or Source in request No. 2.
   * **Deliverable 3: What is the message sent in the ARP Request?  What is the message sent in the ARP Reply?**
     * Request: Who has 192.168.2.1? Tell 192.168.2.2
     * Reply: 192.168.2.1 is at 42:15:a0:09:3a:ce
     *

         <figure><img src="../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
     * This screenshot shows the ARP requests in Wireshark. See the Info tab.&#x20;
2.  Ping another student system on your LAN (We've done this).

    * **Deliverable 4.  Figure out how to create a display filter for ARP traffic only and provide a screenshot showing any ARP traffic related to your neighbor's system.**
      *

          <figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>
      * In this screenshot, you can see the _arp_ display filter used to show only active ARP requests. This screenshot also shows the ARP requests made to 192.168.2.2 and 192.168.2.3.&#x20;
    * **Deliverable 5.  Using a piece of paper and a pencil/pen or even a whiteboard.  Draw out the sequence of ARP request and Response to and from your neighbor.  Take a picture of this with a mobile device and include it as part of your deliverable.**

    <figure><img src="../../.gitbook/assets/image (6) (1).png" alt="" width="563"><figcaption><p>Diagram made in app.diagrams.net</p></figcaption></figure>



1. Repeat the capture and ping- but this time ping Google's Public DNS server - 8.8.8.8
   1.

       <figure><img src="../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

       1. This screenshot shows the ARP and ICMP requests made when pinging 8.8.8.8.&#x20;
   2. **Deliverable 6.  This is important.  DO THIS AS A THOUGHT EXPERIMENT. What do you see in the ARP request and reply? Can you discern the MAC address for the google DNS server or not?  Can you explain what happened?**
      * You cannot identify the MAC address for the Google DNS server, because each hop/gateway replaces the request with its own MAC address. The ARP request only identifies the router that can make the next hop to the Google DNS server, not the MAC address for the Google server itself. This is why we only see our gateway's MAC address.&#x20;



**Optional Windows 10 VM Instructions**

* Install Wireshark from [https://www.wireshark.org/#download](https://www.wireshark.org/#download)
* `arp -d *` to delete all hosts in the Command Prompt
* Open Wireshark
* Ping a valid IP address of your choosing (ex: 8.8.8.8)
* Observe

<br>
