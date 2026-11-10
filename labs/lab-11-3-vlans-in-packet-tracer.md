# Lab 11-3: VLANs in Packet Tracer

**LAB: VLANs in Packet Tracer**

**Part 1 Lab Steps:**

1. Download packet-tracer file vlan-separate [NET-215-vlans-seperate.](https://champlain.instructure.com/courses/2682538/files/407188119/download?wrap=1)pkt
   * In this scenario, the VLANS are for **physically distinct units** that are separated and housed in various office areas within an organization
   * 3 vlans are already created with nodes addressed.
2. To continue the configuration, you will **define the Admin vlan** on the switch
   * Click on the Central Switch and Config tab
   * Click on VLAN database
   * There is a list of current vlans on the right
   * **Create vlan 30 and label it Admin**
3. Next, you will assign VLAN 30 (Admin) to a port on the switch
   * Still on the Central Switch Config tab - select FastEthernet 0/15
   * Port 15 is an Access port but **change the VLAN to 30**
4. Now **connect the Admin switch to the Central switch using a crossover cable**
   * Use port 24 on the Admin switch
   * and connect to port 15 on the Central Switch
5. Next, create two workstations that will be on the Admin vlan
   * Drag two generic PC's onto the workspace
   * Configure their gateway address,  IP addresses, and **netmask** based on the data in the upper left corner.&#x20;
     * **Careful, the netmask is not 255.255.255.0**
   * Connect the PC's to the Admin switch
6. Use ping to check connectivity within vlans and between vlans
   * Nodes in the same vlan should be able to communicate with each other
   * Nodes on different vlans should not.
7. **Submit: Screenshot of a successful ping from 1 Admin PC to the other (2 Points)**

&#x20;

<figure><img src="../.gitbook/assets/image (166) (1).png" alt=""><figcaption><p>This screenshot shows a ping from PC0 to PC1 in Packet Tracer</p></figcaption></figure>

**Lab Steps: Part 2**

1. Open the packet-tracer file VLAN-distributed  [NET-215-vlans-distributed.pkt](https://champlain.instructure.com/courses/2682538/files/407188175/download?wrap=1)[Download NET-215-vlans-distributed.pkt](https://champlain.instructure.com/courses/2682538/files/407188175/download?download_frd=1)
   * In this scenario, the VLANS exist in the same geographic location.
   * This represents the type of layout that might exist in Joyce, Wick, Foster Halls and Miller Information Commons
   * In other words, people in the same building are on different vlans
2. Ping from one faculty PC to another, do the same for student PC to student PC.
   * Systems on the same VLAN can ping each other even if they are on different switches
   * This is because all of the switches have vlans 30 (faculty) and 40 (student) defined **and**
   * The switches are connected via **trunk ports**
3. Examine the configuration of the Joyce Switch
   * Make note of the VLAN Database
   * Make note of the Access port VLAN assignments for the interfaces that the faculty and student PC's are connected to
   * Make note of FastEthernet 0/23. This is the port connecting Joyce to the Central Switch. Notice it is a Trunk port and is supporting all the vlans
4. Using that info, configure the switch for Foster Hall so it will accommodate the student and faculty PC's.
   * The Faculty and Student vlans need to be defined in the database
   * The switch ports connecting the PC's need to be allocated to the proper vlan
   * The switch port you will connect to the Central switch needs to be a **trunk port**
5. Configure the switch port on Central Switch that is connected to Foster as a trunk port
6. Finally, add the proper IP configuration to the Foster student and faculty PC's
7. Foster PC's should now be able to ping other PC's on the same VLAN
8. **Submit: Screenshot of Foster faculty PC successfully pinging Wick faculty PC (3 Points)**
9.

    <figure><img src="../.gitbook/assets/image (167).png" alt=""><figcaption><p>Screenshot of successful ping from faculty .133 from faculty .132</p></figcaption></figure>

SUBMISSION SUMMARY:

* Screenshot of ping between Foster machines for Part 1
* Screenshot of ping between Foster and Wick faculty machines for Part 2
