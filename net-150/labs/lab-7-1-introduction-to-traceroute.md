# Lab 7-1 Introduction to Traceroute

### Introduction to Traceroute&#x20;

Traceroute to 132.198.255.246

#### Champlain Network Structure.&#x20;

The Ireland 017 lab is connected to a default gateway that connects to Champlain College's backbone network. From there packets destined for the Internet travel to our border router and from there to our Internet Service Provider which can forward us to the World.

#### Lab Instructions.

1. Open Wireshark and prepare to capture packets on the Ethernet Interface.
2. Open a command prompt (cmd) and **without pressing enter**, type _tracert  132.198.255.246_
3. Start Wireshark and **as quickly as you can** get back to the command prompt and press enter.
4. Wait for the tracert to finish and stop the Wireshark capture.
5. In the Wireshark filter window (where is says: Apply a display filter ...) type icmp and press enter
   1.

       <figure><img src="../../.gitbook/assets/image (58).png" alt=""><figcaption><p>Wireshark results after running tracert (ICMP Filtered)</p></figcaption></figure>



**Analyze the results**

1, Observe the first Echo request and note the following (**1 point)**:

|                |                 |
| -------------- | --------------- |
| Source IP      | 184.171.151.96  |
| Destination IP | 132.198.255.246 |
| TTL            | 1               |

2\. Examine the following packet (Time-to-live exceeded) and observe the following (**1 point)**

|                |                 |
| -------------- | --------------- |
| Source IP      | 184.171.151.254 |
| Destination IP | 184.171.151.96  |

3\. How many Time-to-live exceeded packets come from the Source IP noted above **(1 point)**.

**3 TTL exceeded packets came from the source IP.**&#x20;

4\. Looking at the Time-to-live exceeded packets, create a list of unique source addresses **AND** the TTL of the preceding Ping Requests. (**2 points)**

| Source IP of Time to Live Exceeded | TTL of preceding ping request |
| ---------------------------------- | ----------------------------- |
| 184.171.151.254                    | 1                             |
| 10.0.0.112                         | 2                             |
| 10.0.2.2                           | 3                             |
|                                    |                               |
|                                    |                               |

5\. At the end of the list there are a number of successful ping request replies. What is the IP Address of the successful replies. (**1 point**)

* **132.198.255.246**

6\. Using Wireshark, capture a ping to 132.198.255.246. What is the TTL for the ping request? **(1 point)**

<figure><img src="../../.gitbook/assets/image (59).png" alt=""><figcaption><p>Wireshark capture of a ping request to 132.198.255.246. Highlighted is the Time to Live (TTL): 128</p></figcaption></figure>

7\. In a paragraph or two, describe **in your own words** how traceroute finds the path of routers between a source and destination IP. **(5 Points)**

* Traceroute exploits the normal behavior of how ICMP echo requests work. To avoid infinite packet recursion, the time to live is used. This number indicates how many hops before the packet should expire and be dropped. Once a packet is dropped, the server that drops the packet sends a request to the IP address sending the packet that the packet was dropped. This reveals the IP address of the router handling the request. Once it identifies an IP address, it then increments the TTL to find the next router on the hop. Once the computer receives a successful echo reply, it knows it has reached the router destination.&#x20;

<br>
