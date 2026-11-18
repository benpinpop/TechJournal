# Lab 12-1 HTTP Capture Class

**Lab 12-1 HTTP Traffic Capture - Class Lab**

**Objectives:** Decode basic HTTP Request and Response using Wireshark

**Capture 1:**

1\. Open Wireshark on your computer.

2\. Start a Wireshark capture on the active network interface.

3\. From your Windows 10 workstation - open a new incognito window and connect to  http://192.168.4.135/index.html

4\. After the page loads, stop the capture and filter for traffic containing the IP address 192.168.4.135

5\. Find the 3 packets of the TCP handshake between your workstation and your server.

* &#x20;**SUBMIT:** Insert screenshot(s) of the handshake packets into a document. (1 Point)
  *

      <figure><img src="../.gitbook/assets/image (168).png" alt=""><figcaption><p>Screenshot of the TCP Handshake</p></figcaption></figure>

6\. Find the packet from the client requesting the index.html page&#x20;

* **SUBMIT:** Insert screenshot(s) of the request packet into the document **and**
  * write out the first line of the request (aka the Start Line) (1 Point)
  *

      <figure><img src="../.gitbook/assets/image (169).png" alt=""><figcaption><p>Screenshot of GET Request</p></figcaption></figure>

      Start Line: GET /index.html HTTP/1.1

7\. Find the response packet from the server that actually contains the HTML page (body of response packet).

* **SUBMIT:** Insert a screenshot of that packet into the document (1 Point)
  *

      <figure><img src="../.gitbook/assets/image (170).png" alt=""><figcaption><p>Screenshot of the HTTP Response</p></figcaption></figure>
* **SUBMIT: Answer the following question:** What is the secret word in the document? (1 Point)
  * guacamole

**Note on Browser Caching:** When you reload a web page in the same session, the server may send a "304-Not Modified" message telling the browser it should load a locally cached copy. So reloading will not work for this lab and you need to open a new browser session - or CTRL-F5 to force the page to reload.

**Submission Summary:**

* **Screenshot 3-way handshake**
* **Screenshot  Capture 1 HTTP Request**
* **Screenshot Capture 1 HTTP Response**
* **Secret Word hidden in page data**
