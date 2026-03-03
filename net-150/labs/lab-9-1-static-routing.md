# Lab 9-1: Static Routing

**Goals:**&#x20;

* Understand the limitations of routers to identify networks that are not directly connected
* Configure simple static routes to allow packets to cross multiple routers to a remote network

**Lab:**

1. Select PC0 and answer the following: **Answer**
   * What is the PC's IP address and Default Gateway?
     * IP address: 192.168.30.3
     * DG: 192.168.30.1
   * Can you ping the Default Gateway?
     * Yes.
   * Can you ping PC1?
     * Yes.
   * Can you ping any other PC's (2-5)?
     * No :(
2. Why do you think the pings to other networks fail? **Answer**
   1. Because there is no routing setup, therefore the Routers don't know where to send the destination packets.&#x20;

**Create Static Routes**: "Routes" tell routers how to reach other networks.  They don't need to include a lot of information - just the network address, subnet mask, and which of it's interfaces to send out of.

1. On R1, go into "config" mode
   * Reminder: Go to CLI, type "enable" and then "config terminal"
   * Then enter:
   * ```
     R1(config)#ip route 192.168.30.0 255.255.255.0 10.10.20.2 

     R1(config)#ip route 192.168.10.0 255.255.255.0 10.10.10.2 
     ```
   * This provides routes to Network 3 and Network 1 respectively
2. On R2, go into "config" mode and enter<br>
   * ```
     R2(config)#ip route 192.168.10.0 255.255.255.0 10.10.20.1 

     R2(config)#ip route 10.10.10.0 255.255.255.0 10.10.20.1 

     R2(config)#ip route 192.168.20.0 255.255.255.0 10.10.20.1 
     ```
3. On R3, based on what you have configured for R1 and R2, what do you think the configuration should be for R3?
   * **Answer:** What are the ip route commands for R3?

```
ip route 192.168.20.0 255.255.255.0 10.10.10.1
ip route 10.10.10.0 255.255.255.0 10.10.10.1 
ip route 192.168.30.0 255.255.255.0 10.10.10.1
```

1. Ping the different PC's, are they able to communicate? **Show screenshot of successful pings**
   1.

       <figure><img src="../../.gitbook/assets/image (60).png" alt=""><figcaption><p>Screenshot of successful pings</p></figcaption></figure>
2. Go to R1 and type "exit" to leave config mode.  The run the following command
   * show ip route
   * **Answer:** Explain what the command output is showing
     *

         <figure><img src="../../.gitbook/assets/image (61).png" alt=""><figcaption><p>Screenshot of <code>show ip route</code> on R1</p></figcaption></figure>


     * The output shows all routing and connected interfaces for external networks. S stands for static routing, whereas C is connected interfaces.&#x20;
       * 192.168.10.0/24 and 192.168.30.0/24 are statically routed through the 10.10 subnets, and everything is fully connected.
3. Repeat this step for R3 and **Answer** same question
   1.

       <figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption><p>Screenshot of <code>show ip route</code> on R3</p></figcaption></figure>
   2. R3s network is directly connected (192.168.10.0/24), and it is directly connected to the router via the Serial interface.&#x20;
4. Imagine a larger internetnetwork with 25 different network segments (subnets). What would the challenge be with using "static routes"? **Answer**
   1. You'd need to configure static routing for each network to each hop, which would be excruciatingly painful because you'd need around 25 commands per router. Multiply that by 25 routers, that's a lot of manual typing. &#x20;

<br>
