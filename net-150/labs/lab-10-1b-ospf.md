# Lab 10-1b: OSPF

## Here are some important OSPF facts:

* Packet Tracer doesn't allow you to configure OSPF through the GUI - everything must be done in the command-line interface (CLI).
* A variety of factors are used to calculate the best path to each LAN, such as speed, cost, and path congestion.
* When the OSPF configurations are made, they use a wildcard mask and an area number.
  * The wildcard mask is the opposite of a subnet mask, where it uses 0-bits to indicate the network ID and 1-bits to indicate an ignoring bit.
  * The area ID indicates which logical area a router is in. If devices are in the same area, they share more detailed information compared to devices not in the same area (they receive summarized information). These ares are interface-specific, and can be any area between 0 and 4294967295 (area 0 is used as a backbone area that all OSPF area must connect with).

## How OSPF works

OSPF assigns unique Router IDs (RID), which allows OSPF-enabled devices to send ping packets to other OSPF-enabled devices, specifically the direct connections. These RIDs can be configured manually or assigned automatically, the latter of which will try to use the highest loopback IPv4 address or the highest interface IPv4 address. When the directly-connected devices, otherwise known as neighbors, ping each other, they exchange link-state advertisements (LSAs); this is similar to a broadcast. All of the LSAs are sent around until every device has all LSAs (aka LSA-flooding). These LSAs are used by the router to build the link-state database (LSDB). Then, the best paths are calculated using the cost of each link and create the SPF tree. The SPF is finally used to update the SPF tree, and this process is only repeated when a change is made on one of the OSPF-enabled devices.

**LAB:**

Using the same starter file from the "Static Route" lab, we will now configure the network using RIP.  This means that the routers will learn about neighboring routers and network through RIP Broadcasts

1. Configuring OSPF involves&#x20;
   * Enabling it on the router
   * and, declaring which of the directly connected networks should be advertised, and in which area (we're using area 0 because this is a small network)
2. Here is the configuration for R2 in our example:
   * From "config" mode type:
     * ```
       router ospf 1
       ```
   * This will now put you in "router config mode"
   * And then specify the networks directly connected to Router 2 along with the wildcard mask
     * ```
       network 192.168.30.0 0.0.0.255 area 0
       ```
     * ```
       network 10.10.20.0 0.0.0.255 area 0
       ```
   * That's it!
3. Repeat Step 2 for R1 and R3
   * **Make sure to update the network statements to specify the correct networks for those routers!**
4. Use the "show ip ospf neighbor" command in administrator mode to check OSPF neighbors (devices directly connected to). **Post Screenshot for each Router**
5. If it is working, all PC's should now be able to ping one another

**Inspect OSPF Routing Table**

1. Go to R2, exit "config" mode, and type "show ip route ospf".  You should see only the OSPF routes in the table. **Post Screenshot**
2. Examine each route in the routing table. The second number after the "/" in the square brackets indicates the OSPF cost.
   1. If multiple routes to a destination exist, OSPF adds only the fastest route to the routing table. If two or more routes have an equal cost, it adds all of them to the routing table in case of load balancing.
3. **Answer:** What is the cost for each route in the table, and what is the lowest-cost network to communicate with?
4. Run the command "show ip ospf 1" (1 equals the process ID). **Post Screenshot with highlighted RID, number of areas, number of interfaces, number of LSAs, and anything else you find important.**
5. Repeat 1-4 for R3 and R1.

**SUBMISSION Summary:**

* **OSPF Neighbors from R1, R2, and R3 (1 point each)**
* **Routing Table from R1, R2, and R3 (2 points each)**
* **Route Cost and Lowest-Cost Network Answer from R1, R2, and R3 (1 point each)**
* **Detailed OSPF configuration from R1, R2, and R3 with highlighted information (2 points each)**

**Add Tech Journal Link:**

* Add an entry for configuring OSPFv2 on Cisco
* Include any troubleshooting steps you had to take

<br>
