# Lab 11-2

**LAB 11-2: DNS and NSLOOKUP**

**Objective:** Observe the function of DNS hierarchy and resolution using the nslookup command

**Lab Prep:**

This lab can be completed on any machine with nslookup installed.

**Lab Steps**

**I. Basic nslookup usage: If you are having problems with DNS request timed out: Run nslookup, hit return, type: server 8.8.8.8 and then make the requested lookup in interactive mode.**&#x20;

1. nslookup can be a simple command to query a name server. Open a terminal and try "nslookup www.champlain.edu" or any other hostname.&#x20;
   * You should see the address of the name server that you asked **and**
   * The IP address answer to the query
2. nslookup also has an interactive mode. Just type "nslookup" and hit enter.
   * You should now be at a ">" prompt
3. Type a hostname and hit enter - it will try and resolve
4. In interactive mode, you can set specific parameters - like the type of Resource Records you want to query (the default are A records).
   * This is done through the "set type=" syntax
   * While in interactive mode, set the type to query the name server records (NS) only
     * set type=ns
     * Then type "champlain.edu."
     * This will give you a response on the name server for the champlain.edu domain
   * With type still set to NS
     * Just enter a period "." in the terminal. This will show you all of the ROOT Zone servers
     * Enter the code for any TLD (Top-Level-Domain) (e.g. edu) **with a period after the code** (for example, "com." or "edu.")
     * Get creative with entries from [https://www.iana.org/domains/root/dbLinks to an external site.](https://www.iana.org/domains/root/db)
     * That will give you the TLD servers for that TLD
5. **SUBMIT: Screenshot of TLD name servers from nslookup (2 points)**
   1.

       <figure><img src="../.gitbook/assets/image (162).png" alt=""><figcaption><p>Screenshot of TLD name servers for cc.</p></figcaption></figure>

**II. MX Records**

1. MX Records are the Resource records that provide the hostname of the mail servers for a domain.
   * For example, if we look at the e-mail address [grandpa@hotmail.com](mailto:gramdpa@hotmail.com)
     * grandpa is the mailbox on a mail server
     * And whatever comes after the @, has to ultimately resolve to an IP address of a mail server
     * Therefore, hotmail.com needs an MX record
2. Use nslookup to resolve MX records by setting the type
   * Lookup the MX record for hotmail.com
   * Lookup the MX record for Champlain.edu
   * Lookup the MX record for mymail.champlain.edu
   * Lookup another mail domain that you may be familiar with
   * **SUBMIT:** **Screenshot of "champlain.edu."** MX records (don't use mymail.champlain.edu, and don't forget the trailing period) (**2 points**)

<figure><img src="../.gitbook/assets/image (164).png" alt=""><figcaption><p>Screenshot of the MX lookup using nslookup for champlain.edu.</p></figcaption></figure>

**III. Querying Specific DNS Servers**

1. It is possible to use nslookup to query DNS servers other than your local one
2. Exit your current nslookup interactive session if needed
   * Ctrl-c or type "exit"
3. Start nslookup again
4. Type "server 8.8.8.8"  (no ='s sign")
   * this will allow you to query Google's Public DNS
   * Try some resolutions, and you should see that 8.8.8.8 is the responding server

**IV. Using "Quad 9" DNS**

1. Quad 9 (9.9.9.9) is another public DNS server
   * Quad9 is a free, public, recursive DNS server that blocks against **known malicious domains**
   * Run through a non-profit and no personal information is collected
   * Malicious domains are continually updated based on malware analysis, compromised web servers, phishing and malware download sites...![](https://champlain.instructure.com/courses/2682538/files/407188169/download?wrap=1)

2\. Use nslookup and set your query to use the 9.9.9.9 server

3\. Now, try and resolve isitblocked.org again - it should come back as "Non-Existent"

**SUBMIT:**

* **Screenshot of using 8.8.8.8 to resolve the hostname "isitblocked.org"**
* **and then, 9.9.9.9 failing to resolve "isitblocked.org" (2 points)**

<figure><img src="../.gitbook/assets/image (165).png" alt=""><figcaption><p>Screenshot of 9.9.9.9 blocking isitblocked.org where 8.8.8.8 resolves.</p></figcaption></figure>

**Submissions:**&#x20;

* **3 Screenshots**&#x20;
  * **TLD servers**
  * **Champlain MX Records**
  * **isitblocked.org resolved by 8.8.8.8 and blocked by 9.9.9.9**
