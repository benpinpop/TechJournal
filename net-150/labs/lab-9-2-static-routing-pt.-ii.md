# Lab 9-2: Static Routing Pt. II

**Lab**:

The class is charged with setting up a network for a small business with 2 sites - West and East.  The organization has been assigned 154.103.16.0/21 as it's network address.  It needs to be subdivided into the following networks:

* SalesWest (300 users) /23
* FinanceWest (200 users) /24
* SalesEast (100 users) /25
* FinanceEast (50 users) /26
* EAST-WEST link for the routers

&#x20;

1. Determine a subnetting scheme that will work for the organization and complete the following table:

<table><thead><tr><th width="126.4000244140625">Name</th><th width="135.5999755859375">Network Address</th><th>Subnet Mask</th><th width="118">Lowest Useable IP</th><th>Highest Useable IP</th><th>IP for Default Router</th></tr></thead><tbody><tr><td>SalesWest</td><td>192.168.2.0/23</td><td>255.255.254.0</td><td>192.168.2.1 </td><td>192.168.3.254</td><td>192.168.0.2</td></tr><tr><td>FinanceWest</td><td>192.168.1.0/24</td><td>255.255.255.0</td><td>192.168.1.1</td><td>192.168.1.254</td><td>192.168.0.2</td></tr><tr><td>SalesEast</td><td>192.168.3.0/25</td><td>255.255.255.128</td><td>192.168.3.1 </td><td>192.168.3.126</td><td>192.168.0.1</td></tr><tr><td>FinanceEast</td><td>192.168.3.128/26</td><td>255.255.255.192</td><td>192.168.3.129</td><td>192.168.3.190</td><td>192.168.0.1</td></tr><tr><td>EAST-WEST</td><td>192.168.0.1/30</td><td>255.255.255.252</td><td>192.168.0.1</td><td>192.168.0.2</td><td>N/A</td></tr></tbody></table>

**Q1: Include a copy of this table in your submission (4 points)**

Once the table is complete, build the following network within Packet Tracer (note: you'll want to use 2960 switches and "PT-Router" routers, and a Serial DTE cable to connect the routers).

![Lab92\_diagram.PNG](https://champlain.instructure.com/courses/2616866/files/388238301/preview)

Configure this network (but don't add routes yet!) using the IP ranges the class settled on from the table above.

**Q2: Explain in your own words what is happening when SalesWest1 tries to ping SalesEast.** This can be a simple list (e.g. #1 SalesWest1 checks the IP of SalesEast to see if it is on the same network using subnet masks...) **(1 point)**

* When SalesWest tries to ping SalesEast:
  * It checks if the IP address is in the local network using the subnet mask
  * If it is in the local network, it uses ARP to find the MAC address and pings it locally
  * If it isn't in the network, it routes it to the default gateway
  * The default gateway attempts to locate the IP address, but it has no route to it, so the packet fails.&#x20;

**Configure Routing**

Based on your work from Lab 9-1, add static routes to the East and West routers to enable pings across the West and East sites.

**Q3: Take a screenshot of a successful ping between SalesWest1 and SalesEast, and include it with your submission. (1 point) Q4: Take a screenshot of a successful ping between FinanceEast and FinanceWest, and include it with your submission. (1 point)**

<figure><img src="../../.gitbook/assets/image (63).png" alt=""><figcaption><p>Screenshot of pings between SalesWest0 --> Sales East &#x26; FinanceEast --> Finance West</p></figcaption></figure>

**Q5: Include in your submission the commands that you entered on the routers to enable connectivity. (1 point)**

```
EAST ROUTER:
Router(config)#ip route 192.168.1.0 255.255.255.0 192.168.0.2
Router(config)#ip route 192.168.2.0 255.255.254.0 192.168.0.2

WEST ROUTER:
Router(config)#ip route 192.168.3.0 255.255.255.128 192.168.0.1
Router(config)#ip route 192.168.3.128 255.255.255.192 192.168.0.1
```

Technically, I could have done `ip route 192.168.3.0 255.255.255.0 192.168.0.1`.
