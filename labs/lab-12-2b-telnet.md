# Lab 12-2b: Telnet

**Objective:** Understand the Request/Response syntax if the HTTP protocol by using the command line to create a direct connection to a HTTP Server and type HTTP Requests.

&#x20;

**Pre-Lab**

Bring up a Kali Virtual Machine to use for the lab

**Goal**

From the command line, use telnet to connect to a web server and retrieve a web page. &#x20;

To do this, you will have to manually type the **HTTP Message Request Start Line and the Host header**. &#x20;

**Hints**

1. You will need to telnet to the server AND specify the port number
2. You will need to do the following QUICKLY to avoid a timeout
3. "Send" (i.e. type into telnet)  GET /index.html HTTP/1.\`
4. "Send" (i.e. type into telnet) HOST: 192.168.4.135
5. since we do not have a DNS entry for the web server, use the ipv4 address for HOST: header

**Challenge:** Retrieve the web page from <a href="http://192.168.4.243/index.html" target="_blank">http://192.168.4.135/index.htmlLinks to an external site.</a> using telnet from the terminal on your Kali system

* **Hint: Google "Use Telnet to Test HTTP" in HTTP 1.1**
  * **Remember, HTTP uses port 80 and not the default telnet port of TCP/23 so need to specify port in you telnet command**
* **Hint #2: Can also review the capture files from previous labs to see the Start Line syntax**
* **Hint #3: Don't forget - the Host header is required in HTTP/1.1**
* **Hint #4: Hint enter twice for a blank line/ending CRLF**

**Submit:**

* Screenshot of successful retrieval of the index.html page via telnet

<figure><img src="../.gitbook/assets/image (171).png" alt=""><figcaption><p>Screenshot of successful retrieval of the index.html page via telnet to 192.168.4.135</p></figcaption></figure>

