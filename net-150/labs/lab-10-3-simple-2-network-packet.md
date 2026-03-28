# Lab 10-3: Simple 2-Network Packet

**Objectives: Build and observe a Simple Network with 2 Networks**

**Lab Steps**

Build the following network within Packet Tracer:

![](https://champlain.instructure.com/courses/2616866/files/390785717/download?wrap=1)

1\. Network address for Foster is 192.168.3.0/24 and Network address for Skiff is 192.168.1.0/24. Configure IP addresses, subnet masks, and default gateways for the router interfaces and the PC and server following that network information.

2\. Ping server from laptop

**Submit: screenshot of successful ping (2 Points)**

&#x20;

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption><p>Screenshot of successful ping requests from Foster to Skiff and Skiff to Foster</p></figcaption></figure>

**Traffic Analysis in Packet Tracer**

1\. Go into "Simulation Mode" in Packet Tracer (stopwatch on lower right)

2\. From Laptop - open up "Web Browser" on Laptop Desktop

3\. Enter the IP address of server and hit "go"

4\. Use Capture/Forward to send to packets hop-by-hop

5\. Continue until you see HTTP Packets in the Simulation Panel

6\. Review Packet Details of a HTTP Packet in the Simulation Panel

**SUBMIT: Screenshot of Details (Inbound or Outbound PDU) of a HTTP packet that includes the Source/Destination MAC, Source/Destination IP Address (2 Points)**

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption><p>Screenshot of HTTP request details from Laptop to Server with MAC and IP addresses highlighted in black</p></figcaption></figure>

**Practice Saving Router config**

1\. Go back to Real-Time mode (clock)

2\. From Router: Config Tab: Save NVRAM

3\. From Router: Got to "Physical Tab" and use power button to turn off router.&#x20;

4\. Power back on by clicking the button again

5\. Use Fast Forward button to get links back

6\. Check router to make sure Interface IP's are still there

7\. **Submit Screenshot of CNCS Router showing IP address on an Interface (2 Points)**

&#x20;

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption><p>Screenshot of saved IP addresses on interface Fa0/0 after restart on Router0</p></figcaption></figure>

## How to use Simulation Mode

Click Simulation Mode on the bottom left to switch.

Use the Show All/None buttons and filter buttons at the bottom to filter out irrelevant packets. From there, you use the play and fast-forward buttons to speed up packets across the network. \
\
Click on a Packet to view its details, including specific OSI layer information.&#x20;

## Saving Configuration on Routers

* Go to Router > Config > Settings
* NVMRAM > Save
* Restart
* Click the Fast Forward Button on the bottom left to speed up the process of rebooting

## Tips and Tricks

* You can Ctrl + Click on a device to place multiple at the same time.
* Spam Esc to exit out of menus as fast as possible
* Use the lightning icon to connect cables as fast as possible without specifying an interface.&#x20;
* Press P to change to ping modes.
