# Lab 4-3: 2 Router Setup

Packet Tracer - Simple 2 Router Lab

**Objective**

Identify the need for routing protocols and their role in internetworks with multiple routers.

**Goals**

* Observe the need and purpose of routing protocols
* Extend the switched network from the previous lab (402) to include a second router
* Configure RIP to support route propagation for non-directly connected networks

&#x20;

**Initial Steps**

1. Open your Packet Tracer File from Lab 4-2&#x20;
2. Add another network/LAN
   * To the right of the 20.20.20.0/24 network, add
     * A Cisco 2950-24 switch
     * 2 new PC's (PC5 and PC6)
3. This LAN will have the network address:  30.30.30.0/24  (netmask 255.255.255.0)
   * Configure the workstations with IP addresses 30.30.30.105 and .106  with a gateway of 30.30.30.1
   * Connect PC's 5 & 6 to the new 2950-24 Switch, using a straight-through cable.  Pick your own FasterEthernet interfaces on the 2950-24
   * Should look like the image below
   * ![](https://champlain.instructure.com/courses/2682538/files/407188317/download?wrap=1)
4. Add another 1841 Router for that LAN
   * Configure Fa0/0 with the IP 30.30.30.1 and mask 255.255.255.0
   * This will be the default gateway for the new LAN
   * Connect the switch to the router's interface Fa0/0 so it looks like the image below
5. Verify that PC5 and PC6 can ping one another - and their gateway

**Preparing to connect the 2 Routers - Save Configuration**

1. The routes will be on their own network connected via serial lines (not Ethernet, note:  this is an example of Network Interface layer that is not Ethernet).&#x20;
2. To connect the two routers, you need to add a serial port to each, but there is a step to do first.
3. The current configuration **must be saved** on **both** routers.&#x20;
4. Under CLI, type exit until you get to the **router# prompt**.
5. Type  **copy run start**
   * Select defaults for Destination filename (hit enter)
   * This saves the running configuration (recent changes) to the startup configuration- so the changes will persist after a reboot
6. **Make sure to copy run start on both routers**

**Add Serial Ports to Routers**

1. Select the Physical Tab on Router 0
2. Click the Power Button to Off (see diagram below)
3. Drag a WIC-1T interface card into the left slot (Slot 1)
4. Turn the power back On
5. Repeat Steps 1-4 on Router 1

<img src="https://champlain.instructure.com/courses/2682538/files/407188167/download?wrap=1" alt="" height="235" width="519">

**Connecting the Routers**

1. Click on Router0 - Config Tab.
   * There is now a Serial 0/1/0 interface
   * Configure that interface to:
     * IP: 1.1.1.1 with mask 255.255.255.252&#x20;
     * That mask (aka /30) limits the number of devices on that network to 2
     * Remember to enable to interface
2. Repeat the previous step on Router 1 with:
   * IP address: 1.1.1.2 mask 255.255.255.252
3. To connect the 2 routers, use the cable that looks like a red lightning bolt between the Serial 0/1/0 interfaces
4. Your network should now look like:
5. ![](https://champlain.instructure.com/courses/2682538/files/407188133/download?wrap=1)

**Testing Communication**

1. PC0 to PC4 should be able to ping one another
2. PC5 and PC6 should be able to ping one another
3. PC0-4 should not be able to ping PC5-6
4. Go to Router0 CLI
   * From the **Router#** type **show ip route**
   * **SUBMIT (1 Point): Record the networks showing up in Router 0's routing table (either via text or screenshot)**
     *

         <figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>This screenshot shows the Router 0 show ip route configuration</p></figcaption></figure>
5. Go to Router1 CLI
   * From the **Router#** type **show ip route**
   * **SUBMIT (1 Point): Record the networks showing up in Router 1's routing table (either via text or screenshot)**
     *

         <figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>This screenshot shows the Router 1 show ip route configuration</p></figcaption></figure>
6. You should see that Router 0 does not know about the 30.30.30.0/24 network
7. And, Router 1 does not know about the 10.10.10.0/24 or 20.20.20.0/24 networks

**Need for Routing Protocols**

1. In order for all PCs to be able to communicate, the 2 routers need to be able to communicate their routing information to each other.  They can then build their routing tables so packets can be directed to the proper interface.
2.  &#x20;

    We will use the Routing Information Protocol (RIP)

    * With RIP, the routers will broadcast their routing tables so that neighboring routers can learn about other networks
3.  &#x20;

    Click on Router 0:

    * In Config, select RIP (Router Information Protocol)
    * You need to add the network(s), so it can advertise them to other routers.
    * Add the networks: 1.1.1.0, 10.10.10.0 and 20.20.20.0
    * **Note:  For the networks , the router will assume a netmask of 255.0.0.0 and use 1.0.0.0, 10.0.0.0, 20.0.0.0, 30.0.0.0 as the network addresses**.&#x20;
      * This is because RIPv1 was a classful protocol and assumes any address starting with and a first octet < 127 is a Class A address.  This is ok for this lab and will still work.
4. Click on Router 1:
   *   &#x20;

       Configure RIP and add the networks 30.30.30.0 and 1.1.1.0.
   * Again, it will likely to convert those to 30.0.0.0 and 1.0.0.0 which is ok.
5. Save the configuration (copy run start) on both routers
6.  &#x20;

    Hit "Fast Forward Time" a few times to allow the RIP broadcasts to go between the two routers
7. All PC's should now be able to ping one another

**Validate Routing Tables and RIP**

1. **SUBMIT (1 Point) Screenshot of routing table (show ip route) on Router 0 showing all of the networks listed**
   1.

       <figure><img src="../.gitbook/assets/image (128).png" alt=""><figcaption><p>This screenshot shows the <code>show ip route</code> command on Router 0.</p></figcaption></figure>
2. **SUBMIT (1 Point) Screenshot of routing table on Router 1 showing all of the networks listed**
   1.

       <figure><img src="../.gitbook/assets/image (129).png" alt=""><figcaption><p>This screenshot shows the <code>show ip route</code> command on Router 1.</p></figcaption></figure>
3. **SUBMIT (1 Point) Successful ping between PC0 and PC6**
   1.

       <figure><img src="../.gitbook/assets/image (130).png" alt=""><figcaption><p>This screenshot shows a successful ping from PC6 to PC0 on the bottom right.</p></figcaption></figure>
4. Switch to Simulation Mode (stopwatch icon in lower right)
   * Click "Edit Filters" and **uncheck** the following
     * IPV4-ARP
     * MISC-STP
     * MISC-CDP
     * MISC-DTP
   * Start Auto Capture/Play and collect data for a few minutes
   * RIPv1 Packets should populate the Simulation Panel
   * ![](https://champlain.instructure.com/courses/2682538/files/407188157/download?wrap=1)
   * Find a Router0 to Router1 packet
   * Click on the colored block for that packet
   * Scroll through the Inbound PDU Details
   * **Submit (1 Point) Screenshot of the Inbound PDU Details**
     *

         <figure><img src="../.gitbook/assets/image (131).png" alt=""><figcaption><p>This screenshot shows the inbound PDU details of a Router0 to Router1 packet in Cisco Packet Tracer</p></figcaption></figure>
   * **Submit (1 Point): Answer the following question: What is the Destination IP address (IP Header) of that packet?  What does that IP indicate?**
     * **The destination IP address is 255.255.255.255, meaning that it is the broadcast address, so it is sending it to all devices.**
   * **Submit (1 Point)**: **Answer the following question: What network information is included in the "Rip Route Packet" section? Why is that information included?**
     *   The information included is the Network Address, Subnet Mask, Next Hop, and Metric.

         <figure><img src="../.gitbook/assets/image (132).png" alt="" width="375"><figcaption><p>This screenshot shows details of a Rip V1 packet from Router0 to Router1</p></figcaption></figure>


     * This information is included so that the router knows where to go next if it comes across an address on that network. The network address tells the other router what network is available. RIP automatically assumes the subnet mask, which is why it is 0.0.0.0. The metric tells it how expensive it is to reach that network. &#x20;
