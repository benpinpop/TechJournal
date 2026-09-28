# Lab 6-2: Simple Subnetting

### Lab 6-2 Simple Subnetting with Packet Tracer

**Objectives:** Demonstrate simple subnetting by dividing a network into 2 subnets

**Goals:**

* Successfully divide a /24 subnet into two /25 subnets
* Correctly configure IP addresses, subnet masks, and default gateway to support a subnetted network on router interfaces and host nodes

**Pre-Lab**:

Open your Packet Tracer File from LAB 4-3: Packet Tracer with Two Routers (alternatively, you can use [this file](https://champlain.instructure.com/courses/2682538/files/407188417/download?wrap=1)[Download this file](https://champlain.instructure.com/courses/2682538/files/407188417/download?download_frd=1)).

**Lab Steps:**

In this lab, you will subnet the 30.30.30.0/24 network into two subnets:&#x20;

* Subnet 1: 30.30.30.0/25
* Subnet 2: 30.30.30.128/25

The end result should look like below, and all PC's should be able to ping one another:

![](https://champlain.instructure.com/courses/2682538/files/407188091/download?wrap=1)

To complete that objective, you will need to do the following:

1. Add a new switch (Switch 3) and two PCs (PC7 and PC8)
2. You will need to update the subnet mask on PC5 and PC6
3. You will need to update the subnet mask of Fa0/0 on Router 1
4. You will need to configure the Fa0/1 interface on Router 1 to be the default gateway for the new subnet
5. You will need to connect Switch 3 to the Fa0/1 interface on Router 1
6. You will need to configure the IP Address, Subnet Mask, and Gateway on PC7 and PC8

**Once configured, PC7 and PC8 should be able to ping all other PC's**

**Submission:**

1. Open the CLI on Router 1:
   * From the **Router#** prompt, type "show ip route"
   * The route table should show that 30.0.0.0/25 is subnetted
   * **Submit screenshot of correct command output** (2 Points)
2. Go to PC8-Desktop-IP Configuration
   * **Submit Screenshot of correct configuration** (2 Points)
3. Ping PC1 from PC8
   * **Submit Screenshot of successful ping** (1 Point)
