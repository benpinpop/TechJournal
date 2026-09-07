# Lab 3-1: ARP Observation Lab

**Objective**: Observe Address Resolution Protocol operations and draw conclusions on how Layer 2 (MAC) and Layer 3 (IP) addresses interoperate

**Goals**:

* Understand how ARP is used between hosts on a LAN
* Recognize the basic flow of ARP
* Identify the role of broadcasts with ARP

**Pre-Lab Setup**

This lab requires the use of a **Kali Linux workstation**. If you do not have one set up, refer to [Lab 1-0: Import VMs](https://champlain.instructure.com/courses/2682538/modules/items/128802855) for instructions on how to do so.



**I. Capture and Analyze an ARP Request**

1. Open a terminal **on your Kali VM**
2. Run the command "ip route" and make note of the IP address of the default gateway. Also note the instructor's workstation is 192.168.x.100 where x is 1 in Skiff, 3 in Foster, and 7 in Joyce.
3. Run the following command (This will delete any saved ARP results):
   * ip neigh flush all (you may need to add 'sudo' to the beginning of the command to get the necessary privileges)
4. Open **Wireshark** in Kali and start a capture
5. Back in the terminal- ping the **Instructor's workstation (in Ireland 017 this is 192.168.1.100)**
6. Stop Capture
7. Analyze Capture for ARP packets:
   * **Answer:** Find the ARP broadcast that your computer used to find the Instructor's MAC address. What is the source MAC address? What is the destination MAC address? (Hint: Data Link Layer Header)
     * I used my own Proxmox for this, using a neighboring Kali with SNAT on 172.16.1.0/16.
     *

         <figure><img src="../../.gitbook/assets/image (124).png" alt=""><figcaption><p>Screenshot of Kali Linux Wireshark of an ARP request to 172.16.1.4 from 172.16.1.3.</p></figcaption></figure>
     * The source MAC address is bc:24:11:7e:7f:ec, and the destination MAC address is 00:00:00:00:00:00
   * **Answer:** Find the ARP reply from the instructor's workstation back to your computer. What is the source MAC address? What is the destination MAC address? (Hint: Data Link Layer Header)
     *

         <figure><img src="../../.gitbook/assets/image (125).png" alt=""><figcaption><p>Screenshot of Kali Linux Wireshark of the ARP reply from 172.16.1.4 to 172.16.1.3</p></figcaption></figure>
     * The source MAC address is bc:24:11:2b:41:97 and the destination MAC address is bc:24:11:7e:7f:ec.
   * **Answer:** What is the message sent in the ARP Request?  What is the message sent in the ARP Reply?
     * The message sent in the ARP request asks who has 172.16.1.4, and tells the device to tell 172.16.1.3 at its MAC address. The message sent in the ARP reply identifies the MAC address of 172.16.1.4.&#x20;
8. Flush the arp cache again with "ip neigh flush all"
9. Repeat the capture and ping- but this time ping Google's Public DNS server - 8.8.8.8
   * **Answer:** What do you see in the ARP request and reply? Can you explain what happened? If there is no arp request/reply try again, but start Wireshark before flushing the cache.&#x20;
     *

         <figure><img src="../../.gitbook/assets/image (126).png" alt=""><figcaption><p>Screenshot of Wireshark ARP request to 172.16.1.1</p></figcaption></figure>


     * I see that the ARP request is made to 172.16.1.1, which is our default gateway. The reason it is doing this is that ARP is a Layer 2 protocol, which only works within the network. We cannot send a packet outside our network using a MAC address (besides the default gateway). Whenever a packet needs to go outside the network, Layer 3 is used, so we need to send our packet to the default gateway for further routing.&#x20;
