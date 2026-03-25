# Lab 14-1: Network Troubleshooting

**Troubleshooting Process:**

1. Gathering information
2. Analyzing information
3. Eliminating possible causes
4. Formulating a hypothesis
5. Testing the hypothesis
6. Solving the problem

**Troubleshooting Methods**

1. The top-down approach
2. The bottom-up approach
3. The divide-and-conquer approach
4. The follow-the-path approach
5. The spot-the-differences approach
6. The move-the-problem approach



**Challenge 1:** [**NET-150-Lab 14-1 Troubleshooting Challenge 1.pkt**](https://champlain.instructure.com/courses/2616866/files/390785723/download?wrap=1)

Foster Laptop should be able to ping Skiff Laptop - but something is wrong!

* Ping requests to the router work
* Ping requests from router to the devices work
  * Either a router issue or a device issue
* Examining the Router configuration doesn't show any issues
* Examining the Skiff Laptop configuration shows no Default Gateway, so we just need to set it to 192.168.1.1
* And we get a successful ping! I think this was a pretty efficient method, and there wasn't too much to look at.&#x20;
*

    <figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Screenshot of a successful ping from Foster to Skiff</p></figcaption></figure>

**Challenge 2:** [**NET-150-Lab 14-1 Troubleshooting Challenge 2.pkt**](https://champlain.instructure.com/courses/2616866/files/390785737/download?wrap=1)[**Download NET-150-Lab 14-1 Troubleshooting Challenge 2.pkt**](https://champlain.instructure.com/courses/2616866/files/390785737/download?download_frd=1)

* The cable connected from the Router to the Switch is red, meaning that the interface isn't configured.
*

    <figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Screenshot of unconfigured and powered off interface (FastEthernet0/1)</p></figcaption></figure>


* We just need to configure it, and we get a good ping!
  *

      <figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Screenshot of Foster sucessfully pinging Skiff</p></figcaption></figure>


* The first ping typically fails due to ARP, so ping it twice before you give up!

**Challenge 3:** [**NET-150-Lab 14-1 Troubleshooting Challenge 3.pkt**](https://champlain.instructure.com/courses/2616866/files/390785729/download?wrap=1)[**Download NET-150-Lab 14-1 Troubleshooting Challenge 3.pkt**](https://champlain.instructure.com/courses/2616866/files/390785729/download?download_frd=1)

* Tried pinging the routers from all devices, but no dice.&#x20;
* Pinging devices in the 10.10 network without the router gets a good ping, so I definitely need to investigate further
* I looked at a lot of the configuration for the devices, and they all seemed right, but then I realized the cables might be mismatched to the wrong ports, and hovering over it shows us that I'm right:
*

    <figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Screenshot of mismatched cables</p></figcaption></figure>


* After rearranging the cables, the devices can now ping each other, and we get successful pings!
  *

      <figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Screenshot of successful pings between devices</p></figcaption></figure>
* I definitely spent a little more time on this one, but I should've moved on quicker after realizing that it was a cable issue, and not actually a configuration issue.&#x20;

**Challenge 4**

* I start by doing a one-hop ping, so pinging from the endpoint device to the router to try and identify the point of failure.
* All the devices can ping each other and the intermediary router, but not the third router/hop.&#x20;
* I made sure to check all the IP addresses and subnet masks to see if they matched to rule out a configuration issue.&#x20;
* At this point, I knew it was likely a route issue. I checked Router2's IP configuration using `show ip route.` The only connections were static and connected, so it wasn't advertising the network via RIP.
* I configured the networks via RIP and got successful pings:
  *   &#x20;

      <figure><img src="../../.gitbook/assets/image (90).png" alt=""><figcaption><p>Screenshot of successful pings across the network</p></figcaption></figure>
* This was likely a Follow the Path approach, and I think this worked generally well. I think the only mistakes/confusion I had in the beginning were that the PC could ping the second router, but that generally made sense. The router is still on the LAN, whereas the third router is a hop outside the main router, and because the network isn't advertised, the packet isn't forwarded.
* I really wouldn't follow another method, as this seems to be working relatively well.&#x20;

**Challenge 5**

<figure><img src="../../.gitbook/assets/image (91).png" alt=""><figcaption><p>Screenshot of successful ping between Clinic PC 1 and Guest Laptop 2</p></figcaption></figure>

* **Description of Troubleshooting Approach you started with and the steps your took (1 Point)**
  * I started figuring out which devices could ping each other, and it seems that devices on the same VLAN could ping each other, but I couldn't ping Guest laptop 2, and it couldn't ping any other devices
  * I assumed it must be a VLAN tagging issue due to the setup, so I hovered over the cable to see the number (Fa0/15) and examined the switch configuration. The VLAN was set to 1 instead of 20, meaning that it didn't have the right VLAN tag. I changed the VLAN tag, and everything was working again.
* **Description of any issues you encountered, mistakes you made, whether another approach would have been better and/or did you combine methods (1 Point)**
  * I definitely should've pinged devices twice before giving up, because I got very confused for a bit when I could ping devices across VLANs. I had already fixed it, and I wasn't sure which solution actually caused the fix.
  * I tried to input a command into the multilayer switch with the "no encapsulation," but that didn't work because it only works on Routers.&#x20;
  * I should have tried one solution at a time, then tested.

<br>
