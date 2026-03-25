# Lab 11-2: VLANs Pt. 2

**Lab:** Using the completed Packet Trace file from Lab 11-1, you should have VLANs similar to our example slide:

![](https://champlain.instructure.com/courses/2616866/files/390785733/download?wrap=1)

&#x20;

**III. Set up Inter-Vlan Routing**

At the end of Lab 11-1, PC's on the same VLAN should be able to ping each other.  But, without a router acting as the default gateway for each of the VLANs/subnets - the PC's cannot ping PC's on different VLANs.

To fix that, you will need to configure the router. This concept is **router on a stick**. You will need to create **sub-interfaces** on a router for your VLANS. These are virtual interfaces and on each sub-interface you can configure an IP address.&#x20;

1. On **3rd Floor Switch Only:**
   * Go to Config Tab GigabitEthernet0/1 and change to Trunk
   *

       <figure><img src="../../.gitbook/assets/image (83).png" alt=""><figcaption><p>Screenshot of GigEth0/2 Trunk Settings</p></figcaption></figure>

       **I am using GigEth 0/2 because GigEth0/1 is in use connecting to the 2nd floor switch.**&#x20;
2. **Connect Router interface FastEthernet0/0 to GigabitEthernet0/1 on 3rd Floor Switch using a straight-through cable**
   1.

       <figure><img src="../../.gitbook/assets/image (84).png" alt=""><figcaption><p>Screenshot showing a connected switch and router using a straightthrough cable. </p></figcaption></figure>
3. **Define the VLANs on the Router as you did on the switches**
   1.

       <figure><img src="../../.gitbook/assets/image (85).png" alt=""><figcaption><p>Screenshot of the defined VLANs on the router</p></figcaption></figure>
4.  **There is an error in the router configuration for the vlan 10 sub which is as follows. There should NOT be a native at the end of the encapsulation and we need to remove it.**&#x20;

    interface FastEthernet0/0.10

    encapsulation dot1Q 10  native

    ip address 192.168.10.1 255.255.255.0
5. To fix this, go to the CLI in packet tracer and type exit until you see **Router#.** If you see Router> you have typed one too many exits and you need to type **enable** to get back to privilege mode.&#x20;
6. We need to enter configuration mode for sub-interface Fa0/0.10 and then remove the encapsulation. We will then create an encapsulation without the native and then add the network interface address. \
   \
   config t\
   interface FastEthernet0/0.10\
   no encapsulation dot1Q 10 native\
   encapsulation dot1Q 10\
   ip address 192.168.10.1 255.255.255.0

<figure><img src="../../.gitbook/assets/image (88).png" alt=""><figcaption><p>Screenshot showing successful input of commands into Router0</p></figcaption></figure>

1. If all goes well, all PC's should now be able to ping!

<figure><img src="../../.gitbook/assets/image (89).png" alt=""><figcaption><p>Screenshot of final configuration and successful ping from ENG-PC1 to ACT-PC3</p></figcaption></figure>

