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
2. Go to R1 and type "exit" to leave config mode.  The run the following command
   * show ip route
   * **Answer:** Explain what the command output is showing
3. Repeat Step 6 for R3 and **Answer** same question
4. Imagine a larger internetnetwork with 25 different network segments (subnets). What would the challenge be with using "static routes"? **Answer**

**Submit Answers to questions and screenshots**

* **6 Answers (1 Point Each)**
* **Screenshot (4 Points)**

<br>
