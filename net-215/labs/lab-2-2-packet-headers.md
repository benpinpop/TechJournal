# Lab 2-2: Packet Headers

Instructions:

1. Download the pcap

2\. For this lab, we will be looking at the raw bytes of the packets, which will be shown in the bottom-most window of Wireshark.

<img src="https://champlain.instructure.com/courses/2682538/files/407188213/preview" alt="wireshark_bytes.PNG" height="377" width="500">

3\. Click on the 'Ethernet II' line in the middle Wireshark window. This will highlight the bytes that make up the Ethernet header within the packet. **Answer the following questions (1 point each):**

* **How many bytes are included in the header?**
  * **14 bytes are in the Ethernet Header:** 84 17 ef eb d1 bb 28 3a 4d 84 e1 7f 08 00
  *

      <figure><img src="../../.gitbook/assets/image (117).png" alt=""><figcaption><p>Screenshot of the Ethernet II header in Wireshark</p></figcaption></figure>
* **Which bytes represent the destination MAC? Which bytes represent the source MAC?**
  * 6 bytes represent the destination MAC: 84 17 ef eb d1 bb
  * 6 bytes represent the source MAC: 28 3a 4d 84 e1 7f
  * The last two bytes indicate the Type, which stands for IPv4.

4\. Now click on the 'Internet Protocol Version 4' header in the middle window. **Answer the following question: How many bytes are included in this header? (1 point)**

* There are 20 total bytes, you can find this in the "header length" field or by counting the total number of bytes.
  * **45** 00 01 6f 02 00 40 00 80 06 44 be 0a 00 00 49    \
    0010 12 dc 95 a6
*

    <figure><img src="../../.gitbook/assets/image (118).png" alt=""><figcaption><p>Screenshot of the IPv4 Header details</p></figcaption></figure>

5\. **Answer the following question: Why is the packet's Ethernet header the first bytes we see in the packet? (1 point)**

* The Ethernet header is the lowest level on the OSI model (Layer 2): the Data Link layer. Because it is the lowest header, it is wrapped/encapsulated last.

6. Download the second file

7\. **Answer the following questions (1 point each):**

* **How many bytes are included in the Ethernet header of the ARP response packet (the second one in the capture)? How many are included in the Ethernet footer (i.e. padding)  of this packet?**
  * **In the Ethernet header, there are 14 bytes, and 18 bytes in padding.**
  *

      <figure><img src="../../.gitbook/assets/image (119).png" alt=""><figcaption><p>Screenshot of the ARP response packet</p></figcaption></figure>
* **Why is there a footer/padding included in the response packet? (Hint: Check out the 'ARP Request' section at** [**https://www.practicalnetworking.net/series/arp/traditional-arp/Links to an external site.**](https://www.practicalnetworking.net/series/arp/traditional-arp/)**!)**
  * **This is because the minimum frame size of an Ethernet frame is 64 bytes. It needs the extra 18 bytes to make it to that minimum. (Yay!)**

<br>
