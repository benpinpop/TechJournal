# Lab 10-1 UDP Transport

**Objective**: Analyze traffic captures to decode UDP headers and observe UDP network communications.

**Lab Steps:**

**DNS and DHCP Examples**

1\. On your Windows 10 Workstation, start a traffic capture on your wired connection (likely Ethernet 6)

2\. Open a command prompt:

* Perform some nslookups on different web servers (e.g. nslookup [www.burlingtonvt.govLinks to an external site.](http://www.burlingtonvt.gov/))
* Run the the following command to renew your IP address lease with the DHCP server
  * ipconfig /renew

3\. Stop the capture

4\. Analyze your capture.  You should see that your computer is quite busy handling multiple communications

5\. Enter "UDP" in the display filter:

* Find the DNS packets for your nslookup
* These are short "request/response" so use UDP.  No overhead of a handshake is required
* **Submit Screenshot of UDP header in a DNS request with source and destination UDP ports visible**
  *

      <figure><img src="../.gitbook/assets/image (159).png" alt=""><figcaption><p>Screenshot of UDP Layer on the DNS request in Wireshark</p></figcaption></figure>
* Find the DHCP Request packet associated with your lease renewal
* **Submit Screenshot of UDP header in a DHCP request with source and destination UDP ports visible**
  *

      <figure><img src="../.gitbook/assets/image (160).png" alt=""><figcaption><p>Screenshot of UDP Header on the DHCP Request in Wireshark</p></figcaption></figure>

**Network Time Protocol Example**

6\. Start a new capture

7\. From command prompt, you will use the w32tm command to query a remote "time" server

* "w32tm /stripchart /computer:time.nist.gov /samples:5"
* This command will compare (stripchart) your workstation's time with that of the NIST server 5 (samples) times

8\. Stop capture and analyze the NTP (Network Time Protocol Packets)

* NTP is another example of a "request/response" protocol using the low overhead of UDP
* **Submit Screenshot of UDP header in a NTP request with source and destination UDP ports visible**
  *

      <figure><img src="../.gitbook/assets/image (161).png" alt=""><figcaption><p>Screenshot of UDP Layer on NTP Requests in Wireshark</p></figcaption></figure>

**SUBMISSION- 3 Screenshots**
