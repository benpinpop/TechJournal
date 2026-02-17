# Lab 5-1: Routing Lab

**Objective:** Configure and observe a simple routed network.

**Goals:**

* Configure a network
* Observe the Layer 2 header changes as a packet crosses a router
* Recognize the role of the default gateway



### **Part 1 - Building the Network**

1\. **Deliverable 1: Build the below network in Packet Tracer. Screen Capture of networks** (1 points)

<figure><img src="../../.gitbook/assets/image (48).png" alt=""><figcaption><p>This screenshot shows the completed packet tracer file</p></figcaption></figure>

Use the Router-PT-Empty. You will need to add three PT-ROUTER-NM-1CFE Modules to the router. To do so, do the following

* Click on the router and then the physical tab. Use the slider to go all the way to the right and click the power button to turn off the router. The green light should go off.&#x20;
* Under modules select the PT-ROUTER-NM-1CFE Module and drag it to the empty slot furthest to the right. Repeat with two more modules placing them in the right most empty slots.&#x20;
* Turn the router back on.
* This will provide you with three fast ethernet interfaces: 0/0, 1/0 and 2/0.

&#x20;

You will need to assign IPs to laptops and router interface. As well as assign default gateways. **Device numbers may not match devices you have.**&#x20;

![Network.PNG](https://champlain.instructure.com/courses/2616866/files/387195221/preview)

&#x20;

2\. Configure the IPs on the router interfaces. You will need 3 different network/IPs  **Deliverable 2: Screen capture of router IP settings.  5 points**

<figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption><p>FastEthernet0/0 IP Configuration</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption><p>FastEthernet1/0 IP Configuration</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (51).png" alt=""><figcaption><p>FastEthernet2/0 IP Configuration</p></figcaption></figure>

Set the appropriate IP's to your workstation'&#x73;**. Workstations IP should be in same network as default gateway.** You should have instructions for doing this in your Tech Journal!

<figure><img src="../../.gitbook/assets/image (52).png" alt=""><figcaption><p>PING ME IP Configuration</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (53).png" alt=""><figcaption><p>PC6 IP Configuration</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (54).png" alt=""><figcaption><p>HELLO IP Configuration</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (55).png" alt=""><figcaption><p>WORLD! IP Configuration</p></figcaption></figure>

Once all of the interfaces are configured, try pinging from _HELLO!_ laptop to _Ping Me_ laptop. **Deliverable 3: Screen capture of HELLO! pinging Ping Me. 1 points**

*

    <figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption><p>Successful ping from HELLO to PING ME</p></figcaption></figure>

&#x20;

Issues and Notes

* **For PCs connected directly to the router, we need the crossover cable.**
* Ensure you add the right modules to the router so you can plug in your devices.
* Press _P_ to turn on ping
* Press _Ctrl_ when selecting a device to place multiple devices at one time. Press Esc to exit placement.

