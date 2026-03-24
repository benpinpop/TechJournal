# Lab 10-1: RIP Lab

### Packet Tracer Class Lab - Understanding RIP

The **Routing Information Protocol** (**RIP**) is one of the oldest distance-vector routing protocols, which uses the hop count as a routing metric. RIP avoids routing loops by employing a limit on the number of hops permitted in a path from the source to a destination. The maximum number of hops permitted for RIP is 15. A hop count of 16 is considered an infinite distance, in other words the route is considered unreachable. Despite this limitation, RIP works great for basic route communications between devices.

## Here are some important RIP facts:

* Cisco routers don't enable RIPv2 by default. To use RIPv2, you must use the ver 2 command in RIP Router Configuration Mode.
* RIP uses hop count as it’s metric.

## How RIP works

With RIP, a router sends its full routing table to all other connected routers every 30 seconds. Triggered updates can also occur if a router goes down before the 30-second timer has expired.

RIP performs "routing by rumor" and is more prone to loops than other routing protocols. That's because a RIP router sends its entire routing table to every other router. All other routers do the same, and because there's no real neighbor relationship or calculation of routes, the routers have little firsthand knowledge of available networks.

**LAB:**

Using the same starter [Packet Tracer File](https://champlain.instructure.com/courses/2616866/files/388238297/download?wrap=1)[ Download Packet Tracer File](https://champlain.instructure.com/courses/2616866/files/388238297/download?download_frd=1)from the "Static Route" lab, we will now configure the network using RIP.  This means that the routers will learn about neighboring routers and network through RIP Broadcasts

1. Configuring RIP involves&#x20;
   * Enabling it on the router
   * and, declaring which of the directly connected networks should be advertised
2. Here is the configuration for R2 in our example:
   * From "config" mode type:
     * ```
       router rip
       ```
   * This will now put you in "router config mode"
   * Then specify the version with
     * ```
       version 2
       ```
   * And then specify the networks directly connected to Router 2
     * ```
       network 192.168.30.0
       ```
     * ```
       network 10.10.20.0
       ```
   * Thats it!
3. Repeat Step 2 for R1 and R3
   * **Make sure to update the network statements to specify the correct networks for those routers!**
4. If it is working, all PC's should now be able to ping one another
5. Go to R2, exit "config" mode, and type "show ip route".  You should see all of the the networks in the table. **Post Screenshot**
   1.

       <figure><img src="../../.gitbook/assets/image (66).png" alt=""><figcaption><p>R2 - IP Route Command Output</p></figcaption></figure>
6. Repeat Step 5 for R1 and R3.   **Post Screenshots**
   1.

       <figure><img src="../../.gitbook/assets/image (67).png" alt=""><figcaption><p>R1 - IP Route Command Output</p></figcaption></figure>
   2.

       <figure><img src="../../.gitbook/assets/image (69).png" alt=""><figcaption><p>R3 - IP Route Command Output</p></figcaption></figure>

**Inspect RIP Activity**

1. In Packet Tracer - switch to "Simulation Mode" (Stopwatch icon in Lower Left)
2. Under Event List Filters - Visible Event - Click Show All/None
3. Then click Edit Filters - and Select RIP
4. Click the "Capture/Forward" button in the lower center of the screen repeatedly. You should see RIP packets traversing the network.
5. In the upper right Event List - find a packet for RIPv2 from R1 to R2
6. Click the colored "info" box (in the type section) to display the packet details.
7. Click the Inbound PDU Details tab
8. Scroll down to RIP Route Packet section
   * **Post Screenshot**
     *

         <figure><img src="../../.gitbook/assets/image (70).png" alt=""><figcaption><p>Screenshot of RIP Packet from R1 --> R2 in simulation mode</p></figcaption></figure>
   * **Answer:** Describe what is included in the packet details for the RIP v2 protocol section
     * The RIP packet contains the following information:
       * The network address
       * Subnet Mask
       * Next hop to reach the designated network address (i.e., R2 10.10.20.2 needs to forward the packet to 10.10.20.1 to reach 10.10.10.0/24)
     * This information is repeated for all networks attached to R1, including 192.168.10.0 and 192.168.20.0. It does not include the 192.168.30.0 because that's R2s network.&#x20;
9. Repeat 5-8 for a RIP packet from R3 to R1
   * **Post and Answer**
     *

         <figure><img src="../../.gitbook/assets/image (71).png" alt=""><figcaption><p>Screnshot of RIP packet from R3 --> R1 in simulation mode</p></figcaption></figure>
     * The RIP packet contains the following information:
       * The network address
       * Subnet mask
       * Next hop to designated network address
     * So R3 advertises 192.168.10.0 to the public, and allows R1 to access it through 10.10.10.2.&#x20;

## Troubleshooting

* Use the `enable` command to enter the terminal so that you don't get stuck in an infinite loading loop when you put in a command.
* Use `config terminal` to enter router configuration and skip the router asking you about a terminal.
* Make sure to advertise both inside and outside the network, or else RIP will not work.

## Configuring Rip

```
# Pre-requisite commands if not in configuration mode or priveleged mode
enable
config terminal

router rip
version 2
network <NETWORK_ADDRESS>
```
