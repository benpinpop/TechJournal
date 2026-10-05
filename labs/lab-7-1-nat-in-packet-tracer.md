# Lab 7-1: NAT in Packet Tracer

**Objective:** Using a simplified model of the Skiff and Foster 202 Labs, configure simple NAT (PAT) to access an Internet Web Server

**Goals:**

* Observe Layer 3 Header changes as a packet crosses a NAT router
* Configure Cisco router for IP masquerading using PAT

**LAB Steps**

1. Open Lab 7-1 Starter file: [NET-215-NAT-Packet-Tracer-Starter-with nat interfaces.pkt](https://champlain.instructure.com/courses/2682538/files/407188447/download?wrap=1)[Download NET-215-NAT-Packet-Tracer-Starter-with nat interfaces.pkt](https://champlain.instructure.com/courses/2682538/files/407188447/download?download_frd=1)
2.  Examine he network configuration. Skiff 100 and Foster 202 networks are on private networks (192.168.1.0/24 and 192.168.3.0/24 respectively)

    <img src="https://champlain.instructure.com/courses/2682538/files/407188123/download?wrap=1" alt="" height="335" width="664">
3. We want to configure NAT on the Cyber.Local Router so that all Skiff and Foster pc's can "share" the public Champlain address 216.93.144.10 on the Internet
4. To do that, you need to finish configuring the cyber.local router
   * Click on cyber.local router and go to CLI Tab
   * Use proper commands to get to the Router#(config) prompt
     * You made need to type "enable" and then "config t"
     * or "exit" if at the Router(config-if)# prompt
5. First step is to create an Address Pool called "champ" for the Public IP addresses that 192.168 clients can use. We only have 1 IP in the pool (216.93.144.10) as we are setting up PAT. So you type that IP twice- as the start and end of the pool

```
Router(config)#ip nat pool champ 216.93.144.10 216.93.144.10 netmask 255.255.255.0
```

6\. Next, create an access-list  called "1" that defines which internal IP's can use the Public IP pool champ. We are allowing both Skiff and Foster so can simplify and use 192.168.0.0/16 to cover both. **Note:** This command uses Wildcard Subnet Mask - 0.0.255.255

```
Router(config)#access-list 1 permit 192.168.0.0 0.0.255.255
```

7\. Assign the pool and access rule to interfaces with a nat statement - basically saying that access-list 1 (192.168 addresses) can be translated to the PAT IP' from pool "champ" when going from the "inside" interfaces (Skiff and Foster)  to "outside" interfaces (Internet). **Overload** states that the IP can be used by many (up to 64,000) clients.

```
Router(config)#ip nat inside source list 1 pool champ overload


```

If PAT is working, you should be able to ping the Burlington Telecom server from multiple PC's!

**Submissions**

**I. Capture ICMP (3 Points)**

1. Put Packet Tracer in Simulation Mode (Stopwatch in Lower Right)
2. Under Event List Filters - Click Show All/None - to uncheck all protocols
3. Then click Edit Filters and Select ICMP (ICMP should be the only one selected)
4. Ping the Burlington Telecom Server IP Address (104.27.144.81) from the Skiff 3 Workstation
5. Hit capture/forward a few time as the ICMP packet traverses the network.
6. In the Simulation Panel - find the packet that says&#x20;
   * Last Device: -
   * At Device: Skiff 3
   * Click the colored Info block
   * This is the packet as it leaves the PC - make note of the SRC IP (and layer 2 MAC addresses)
   * **Take Screenshot of OSI Model Layers**
7. Next, find the packet that says&#x20;
   * Last Device: Skiff 100 Switch
   * At Device: Cyber.Local Router
   * Click the colored Info block
   * This is the packet as crosses the router- make note of the SRC IP (and layer 2 MAC addresses) **changes** between inbound and outbound - **this is NAT at Work!**
   * **Take Screenshot of OSI Model Layers showing In and Out Layers**
8. Finally, Capture/Forward until the ping response goes all the way back to Skiff 3. Find the packet that says&#x20;
   * Last Device: Burlington Telecom
   * At Device: Cyber.Local Router
   * Click the colored Info block
   * This is the packet as it returns to Cyber.Local - make note of the **DST** IP header as it crosses ti router. This is **this is NAT response translationat Work!**
   * **Take Screenshot of OSI Model Layers showing In and Out Layers**

**II. Show NAT Translation Table (2 Points)**

1. Return Packet Tracer to Realtime Mode (Clock in Lower Right)
2. Click on a PC and go to Desktop Tab
3. Open the Web Browser and inter 104.27.144.81 to see the BT Test Webpage
4. Repeat steps 1-3 on at least 4 PC's
5. Then, to view the NAT Table that the router is using to track sessions:
   * Go to Cyber.Local router and  get the the Router# prompt (type exit if at Router(confg)#)
   * Then type the following command
   * ```
      Router#sh ip nat translations 
     ```
   * This shows the NAT Table and how TCP ports are used to track connections for the different Skiff and Foster Clients all using the same 216.93.144.10 address!
   * Table headings should look like the example below - but using the IP addresses from our network

```
Pro  Inside global     Inside local       Outside local      Outside global
icmp 50.0.0.1:1        192.168.0.7:1      20.0.0.2:1         20.0.0.2:1
icmp 50.0.0.1:2        192.168.0.7:2      20.0.0.2:2         20.0.0.2:2
```

6\. **Take Screenshot of sh ip nat translations output**
