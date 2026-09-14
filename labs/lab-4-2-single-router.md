# Lab 4-2: Single Router

#### Packet Tracer - Single Router Lab

**Objective:** Review the role of routers in networking and configure a simple routed network

**Goals:**&#x20;

* Gain more experience with switching and routing technology and Packet Tracer.
* Extend the switched network from the previous lab (3-4) to include 2 switches, and  a router.

**Steps**

1. Use one of the following Packet Tracer files to start:
   * For Packet Tracer 7.2.1: Use [this file](https://champlain.instructure.com/courses/2682538/files/407188275/download?wrap=1)[Download this file](https://champlain.instructure.com/courses/2682538/files/407188275/download?download_frd=1).
   * For Packet Tracer 7.3 or newer: Use [this file](https://champlain.instructure.com/courses/2682538/files/407188383/download?wrap=1)[Download this file](https://champlain.instructure.com/courses/2682538/files/407188383/download?download_frd=1).
2. Check the network addresses on the PC's from 10.10.100.X and make sure that 10.10.10.1 is set as the gateway.
   * Click on a PC - Desktop - IP Configuration to review/edit
3. Add another Cisco 2950-24 switch
4. Add a new generic PC (PC4) and connect to the new switch on port Fa0/4
   * Assign an ip address of 10.10.10.104 to PC4 and the same mask and gateway as the other PC's
5. Connect the 2 Switches with **a crossover cable (dotted line-cable in** PT) using port **Fa0/1 on both switches**
6. Ensure that all PC's can successfully ping one another before moving on.

Should look like:

![](https://champlain.instructure.com/courses/2682538/files/407188415/download?wrap=1)

&#x20;

**Creating a Second Network**

1. Next step is create a separate network using a different address (20.20.20.0/24)
2. Change the IP configuration of PC4 with the following info:
   * IP: 20.20.20.104
   * with a gateway of 20.20.20.1 and netmask 255.255.255.0
   * Should look like:
   *

       <img src="https://champlain.instructure.com/courses/2682538/files/407188089/download?wrap=1" alt="" height="238" width="474">
3. Can it ping the machines on the 10.10.10.0 network?
   * It should not work
   * This is because switches operate using MAC addresses
   * In order to communicate between 2 networks, a router is necessary.  The router operates at Layer 3 of the OSI model and uses the Internet Protocol to send packets where they need to go.
4. Insert a 1841 router between the 2 switches.
   * These routers have 2 Ethernet ports and you are going to use them to connect to the 2 networks.
5. Connect a straight-thru Ethernet cable between the Switch on the 10.10.10.0/24 network and FastEthernet  port 0/0 on the router
6. Connect a straight-thru Ethernet cable between the Switch on the 20.20.20.0/24 network and FastEthernet  port 0/1 on the router
7. Remove the crossover cable between the 2 switches
   *

       <img src="https://champlain.instructure.com/courses/2682538/files/407188131/download?wrap=1" alt="" height="219" width="379">
8. Click on the Router - Config Tab
   * on the Fastethenet 0/0 configuration, enter the address :  10.10.10.1 and netmask 255.255.255.0
   * This interface will act as the Gateway for the 10.10.10.0/24 network - so is assigned the Gateway IP of 10.10.10.1
   * Click the "on" box in the upper right to enable the interface
9. Do the same for the FastEthernet 0/1 config, using 20.20.20.1&#x20;
   * the Gateway address for the 20.20.20.0/24 network
   * Make sure to turn the interface "on"
   * Watch the equivalent CLI (Command Line Interface) window at the bottom of the screen as the configuration takes place.
10. When all the lights go green, you should be able to ping between the client nodes on the 2 networks.&#x20;
11. Open the CLI window on the Router
    * You need to be at the **router#** prompt
      * If the prompt is **router(conf)#** type **exit** or if at **router(conf-if)#** type **exit** twice until you return to the **router#** prompt
    * Type "**show ip route**" and it will print the routing table.&#x20;
    * The bottom two rows with the C in front represent the current routes. &#x20;
    * The C indicates that the networks are Directly **C**onnected to the router
12. **SUBMIT: A screenshot of the "show ip route" command with the current routes.**
    1.

        <figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
