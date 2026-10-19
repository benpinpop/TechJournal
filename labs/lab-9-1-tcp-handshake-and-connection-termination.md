# Lab 9-1: TCP Handshake and Connection Termination

## Deliverables

SUBMIT: Take a screenshot of the 3 packets for the TCP handshake (1 point)

<figure><img src="../.gitbook/assets/image (150).png" alt=""><figcaption></figcaption></figure>

3\. What is the TCP Port used by the client/browser? (Hint: Source on SYN)

* 1093 and 33575 (but there's a double SYN), and the first SYN is 1093.

4\. What is the TCP Port used by the web server? (Hint: Destination on SYN)

* 80\.

**5. Highlight the SYN packet and right-click the Sequence Number**

Select Protocol Preferences

Uncheck "Relative sequence numbers"

6\. **SUBMIT: What is the initial Sequence # for communication from the Browser to the Server? (1 Point)**

*

    <figure><img src="../.gitbook/assets/image (155).png" alt=""><figcaption><p>Screenshot of TCP SYN Packet</p></figcaption></figure>


* 3656195473\.

**SYN/ACK Packet**

**SUBMIT: What is the initial Sequence # for communication from the Server to the Browser? (1 Point)**

*

    <figure><img src="../.gitbook/assets/image (153).png" alt=""><figcaption><p>Screenshot of TCP SYN/ACK Packet</p></figcaption></figure>
* 1563605659

**SUBMIT: What is the Ack# indicating that the packet from Browser to Server was received? (1 Point**

* 3656195474\. See the screenshot above.

**Highlight the ACK (3rd packet in Handshake)**

**SUBMIT: What is the Ack# indicating that the packet from Server to Browser was received? (1 Point)**&#x20;

<figure><img src="../.gitbook/assets/image (154).png" alt=""><figcaption><p>Screenshot of TCP ACK Packet</p></figcaption></figure>

* 1563605660\.

#### **Part 2 - FIN Flag and Session Termination**

**Create a new Simple Capture:**

1\. Open a **another new** **Incognito** browser tab and type: http://www.testingmcafeesites.com/ but don't hit enter yet

2\. Start a Wireshark Capture

3\. Go back to browser tab and hit enter

4\. **After page loads - close the tab - this will terminate the session**

4\. Then Stop Capture

**Analyze Capture:**

1\. Filter the capture file if needed (ip.addr==100.21.215.181)

2\. Take a screenshot of the 3 or 4 packets for the the Session Termination&#x20;

* A FIN is sent in each direction (browser to server and server to browser)
* Each side also acknowledges the FIN with an ACK&#x20;
* **SUBMIT Screenshot (1 Point)**
  * **Note that there may be multiple FIN/ACKs here; make sure to include at least at least one FIN/ACK sent from the browser to the server and one from the server to the browser.**

<figure><img src="../.gitbook/assets/image (156).png" alt=""><figcaption><p>Screenshot of FIN/ACK handshake.</p></figcaption></figure>

3\. Right-click within the TCP Header in Wireshark - Protocol Preferences - Check "Relative Sequence Number"

4\. Based on the Sequence and Ack #'s found in the FIN/ACK packets you included in your screenshot:

* **SUBMIT: How many bytes were sent from browser to server? (1 Point)**
  * **453 Bytes**
* **SUBMIT: How many bytes were sent from server to browser? (1 Point)**
  * **2782 bytes.**



<figure><img src="../.gitbook/assets/image (158).png" alt=""><figcaption><p>Screenshot of Seq and ACK Numbers in Wireshark.</p></figcaption></figure>

**SUBMIT:** Screenshot and Answers to questions
