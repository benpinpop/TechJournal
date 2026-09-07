# Lab 3-1: ARP Observation Lab

**Objective**: Observe Address Resolution Protocol operations and draw conclusions on how Layer 2 (MAC) and Layer 3 (IP) addresses interoperate

**Goals**:

* Understand how ARP is used between hosts on a LAN
* Recognize the basic flow of ARP
* Identify the role of broadcasts with ARP

**Pre-Lab Setup**

This lab requires the use of a **Kali Linux workstation**. If you do not have one set up, refer to [Lab 1-0: Import VMs](https://champlain.instructure.com/courses/2682538/modules/items/128802855) for instructions on how to do so.

#### **0. Please answer the questions. A screen shot or snip is not an answer to the question. It is a picture.**&#x20;

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
   * **Answer:** Find the ARP reply from the instructor's workstation back to your computer. What is the source MAC address? What is the destination MAC address? (Hint: Data Link Layer Header)
   * **Answer:** What is the message sent in the ARP Request?  What is the message sent in the ARP Reply?
8. Flush the arp cache again with "ip neigh flush all"
9. Repeat the capture and ping- but this time ping Google's Public DNS server - 8.8.8.8
   * **Answer:** What do you see in the ARP request and reply? Can you explain what happened? If there is no arp request/reply try again, but start Wireshark before flushing the cache.&#x20;

**Submit: Answers to questions**
