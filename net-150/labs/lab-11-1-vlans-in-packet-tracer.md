# Lab 11-1: VLANs in Packet Tracer

![](https://champlain.instructure.com/courses/2616866/files/390785733/download?wrap=1)

&#x20;

**I. Configure Switchports for VLANs**

1. On 1st Floor Switch, Go to Config/VLAN Database and add the VLANs the switch will support:
   * VLAN Number: 10 Name: ENG
   * VLAN Number: 20 Name: MKT
   * VLAN Number: 30 Name: ACT
2. Then, configure which ports are in which VLAN from Config tab by changing the VLAN number for the Access Port configuration per interface
   * FastEthernet 0/1 can be VLAN 10 (ENG)
   * FastEthernet 0/2 can be VLAN 20 (MKT)
   * FastEthernet 0/3 can be VLAN 30 (ACT)
3. Then, configure the Trunk port that will be used to connect the switch to the 2nd Floor Switch
   * GigabitEthernet 0/1 change to Trunk and add VLANs 10, 20, and 30 (leaving the other default VLANs checked is fine)
4. Repeat 1-3 on 2nd Floor and 3rd Floor switches
   * **Note:** On 2nd Floor switch, you will need to configure both GigabitEthernet 0/1 and Gigabit/Ethernet 0/2 as Trunk ports (step 3) as it connects to two switches

**II. Connect Devices**

1. Assign Appropriate IP configurations to the PC's
   * ENG network is 192.168.10.0/24 and the default gateway will be 192.168.10.1
   * MKT network is 192.168.20.0/24 and the default gateway will be 192.168.20.1
   * ACT network is 192.168.30.0/24 and the default gateway will be 192.168.30.1
   * Remember, every PC needs a unique address
2. Connect PC's to the switch on their floor.
   * **Make sure to connect the PC to the Port on the switch that is in their VLAN!**
3. Connect switches to each other using **Crossover Cables** and the configured Trunk ports
4. If everything is connected and addressed correctly
   * All PC's on the same VLAN should be able to ping each other
   * But, PC's on different VLANs (even on the same switch) should not be able to ping
5. **At this point, All PC's on the same VLAN should ping one another - BUT PC's on different VLANs should not be able to ping one another**

**SUBMIT:**

* Screenshot of ENG-PC1 pinging ENG-PC2 (2 Points)
* Screenshot of MKT-PC2 pinging MKT-PC3 (2 Points)
* Screenshot of ACT-PC1 pinging ACT-PC3 (2 Points)

<figure><img src="../../.gitbook/assets/image (82).png" alt=""><figcaption><p>Screenshot of successful pings and failed ping across VLANs</p></figcaption></figure>

* Answer to question: Why can't PC's on different VLANs ping one another? (3 Points)
  * PCs on different VLANs cannot ping each other because the Switch/networking devices drop the packet. It knows that the other device is on a different VLAN, and therefore refuses to send the packet. It's a virtual local network, and all packets sent from a VLAN'd device are tagged with the VLAN ID. If the VLAN ID is different, then no packet is sent :(<br>

## Configuring VLANs via CLI

```
enable
configure terminal 

# Creating a VLAN by ID
vlan <VLAN_ID>
 name <VLAN_NAME>
 
# to exit
end 

# Setting a port to access or trunk
interface FastEthernet0/<PORT_NUMBER> # Select the itnerface
switchport mode <trunk|access> # Set mode

# Set VLAN ID
switchport access vlan <VLAN_ID>

# Removing/Adding allowed VLAN IDs for Trunk Ports
switchport trunk allowed vlan <remove|add> <VLAN_ID>
```
