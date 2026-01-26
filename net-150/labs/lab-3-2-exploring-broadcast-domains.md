# Lab 3-2: Exploring Broadcast Domains

**Remember, for each lab your tech journal should include:**

* _A brief (one sentence) summary describing what you did in the lab._
  * _In this lab, we examined Wireshark captures from two separate devices and identified why MAC addresses on different networks will only display as the default gateway MAC address._&#x20;
* _Any commands or instructions that you found useful and will need to use again in the future._
  * _ip a_
* _Any problems you ran into during the lab, and what troubleshooting steps you took to fix them._
  * _**Read the instructions**_



**I. Analyze Traffic to a Remote Network (different LAN)**

1. Open a Command Prompt (Windows) or Terminal (Linux)&#x20;
2. Open Wireshark and start a capture
3. Back in the Command Prompt/Terminal- ping the Google Public DNS server (8.8.8.8)
4. Stop Capture
5. **Deliverable 1**: Analyze the ICMP  Response from Google:
   *

       <figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption><p>This screenshot shows the ping requests made from 192.168.2.2 to 8.8.8.8 in Wireshark</p></figcaption></figure>
   * Answer: What is the source MAC address? What is the destination MAC address? (Hint: Data Link Layer Header)
     * The source MAC address is bc:24:11:e3:b3:cd.
     * The destination MAC address is 42:15:a0:09:3a:ce
     *

         <figure><img src="../../.gitbook/assets/image (37).png" alt=""><figcaption><p>This screenshot shows the source and destination MAC addresses in Wireshark</p></figcaption></figure>
   * Answe&#x72;**:** Does the source MAC address look familiar from prior labs? Do you think it is the Google Server's MAC address?
     * Yes, it is the MAC address of our default gateway. It is not the Google server's MAC address. You can see in the ARP requests that 192.168.2.1 is at the destination MAC address. This is because your device only knows the MAC addresses of the devices on the local network and has to contact the gateway to forward the packet. The gateway only knows the MAC addresses of the devices it is in communication with, etc.&#x20;
     *

         <figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption><p>This screenshot shows an ARP reply, identifying 192.168.2.1 (gateway) at our destination MAC address for 8.8.8.8</p></figcaption></figure>

**II. Examine both sides of a ping**

1. Find a partner in class and get their IP address.
   1. I set up another Debian workstation named debian-net1, and assigned it to the CHAMP3 192.168.2.x subnet. The IP address for the device is 192.168.2.4
   2.

       <figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption><p>IPAM display of the CHAMP3 Subnet on Proxmox</p></figcaption></figure>
2. On your workstation, start a wireshark capture, ping your partner's IP, and stop the capture
3. On your workstation, analyze the capture
   * **Deliverable 2:** What are the source and destination MACs in the ping reply
     *

         <figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption><p>This screenshot shows the source and destination MAC address in the ping reply in Wireshark</p></figcaption></figure>
     * The source in the reply is bc:24:11:41:d2:f0
     * The destination (our Kali machine) is bc:24:11:e3:b3:cd
4.  What is your partner's MAC address?&#x20;

    * **Deliverable 3:** Does the MAC address match the address from you traffic capture? If not - what do you think happened?
    * The MAC addresses seem to match in both traffic captures, as seen below.&#x20;

    <figure><img src="../../.gitbook/assets/image (41).png" alt=""><figcaption><p>This screenshot shows the <code>ip a</code> command on the debian-net1 partner machine. Highlighted is the MAC address: <code>bc:24:11:41:d2:f0</code></p></figcaption></figure>

**III:  Capture both sides of the ping request**

1. Start a Wireshark capture on both PCs and let it run
   1. **So, at this point in time, I did not realize we would need to run Wireshark on the other machine, so I am now creating a second Kali Virtual Machine to use.**&#x20;
2. From a command prompt on your workstation, ping your partner's IP address
3. Stop the captures on both Workstations
4. Find and compare the ICMP traffic on both devices
5. **Deliverable 4:**
   1. On your workstatio&#x6E;**,** what is the source and destination MACs from the pings?
      1.

          <figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption><p>This screenshot displays the MAC addresses on the Kali workstation in Wireshark. This device sent the ping requests.</p></figcaption></figure>
      2. The Source is bc:24:11:e3:b3:cd.
      3. The destination is: bc;24:11:d7:4d:b4
   2. On your partner's workstatio&#x6E;**,** what is the source and destination MACs from the pings?
      1.

          <figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption><p>This screenshot displays the MAC addresses on the Kali1 workstation in Wireshark. This device received the ping requests.</p></figcaption></figure>
      2. The Source is bc:24:11:e3:b3:cd
      3. The destination is bc:24:11:d7:4d:b4
6. **Deliverable 5:**  Why do you think they are different OR THE SAME?
   1. They are the same, because it is the same packet. The request packet is sent and logged in Wireshark on _Kali_ and received by _Kali1._ They do not modify or flip the packets, which is why the MAC addresses are (and should be) the same. They are also the same because we are on the same network. The MAC address is only replaced with the default gateway when pinging other devices not on the network.&#x20;

<br>
