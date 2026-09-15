# Assignment 4-1: Interior Routing Protocols

**Interior Routing Assignment**

**Routing Information Protocol v2 (RIP v2)**

Do some research into RIPv2 and review the protocol header information to answer the following questions (**make sure to include citations!**)

RIPv2 Fields

1. The job of any routing protocol is to provide a mechanism for exchanging information about routes so routers can keep their routing tables up-to-date. Describe in your own words (a few sentences and/or detailed bullet points) the mechanism RIP uses so that routers in a network can build their routing table. **(2 Points)**
   1. The mechanism that RIP uses is a broadcast update system. Every 30 seconds, the routers advertise their entire routing tables to one another and what networks they have available. This means that changes slowly propagate to the entire network.
2. Describe in your own words how RIP uses the Route Distance Metric (**1 Point)**
   1. RIP uses the Route Distance Metric by counting each Router as one hop. One hop = One metric point. The limit for the metric is 15, and after 16, the destination is unreachable. So you pass through three routers to get to your destination, the distance metric is 3.
3. Describe in your own words (a few sentences or detailed bullet points) the limitations of RIP on a larger network **(2 Points)**
   1. RIP has a really slow convergence time, as the network is only advertised every 30 seconds. RIP also needs to be manually setup; it's not a dynamic routing protocol, so you have to setup every router with every network, which kind of sucks... On top of that, because it has a max hop count of 16, it just does not scale well to larger networks.&#x20;

[https://www.geeksforgeeks.org/computer-networks/routing-information-protocol-rip/](https://www.geeksforgeeks.org/computer-networks/routing-information-protocol-rip/)

&#x20;

**Open-Shortest Path First (OSPF)**

OSPF is a very popular interior routing protocol and is widely used in larger enterprises.

1. Describe in your own words (a few sentences and/or detailed bullet points) the mechanism OSPF uses so that routers in a network can build their routing table and how it differs from RIP v2. **(2 Points)**
   1. OSPF advertises its network whenever it needs to update, rather than every 30 seconds like RIP does. OSPF uses Link State Advertisements (LSAs), which allow the network to converge much faster. The router keeps an understanding of the network through a Link State Database. Everyone gets an update of the entire network through LSA flooding as the network is updated and changes are propagated through the network.
2. Describe in your own words how OSPF uses the "Cost" Metric (**1 Point)**
   1. Cost is calculated not by hops, but by the bandwidth of the routers along the way. The reference bandwidth is usually set and then divided by the link bandwidth. The higher the link bandwidth, the shorter the cost. So if the connection is Gbps, then the cost will be much lower to send. The calculation is:
      1. $$Cost = (Reference Bandwidth/LinkBandwidth)$$

&#x20;

[https://www.geeksforgeeks.org/computer-networks/open-shortest-path-first-ospf-protocol-fundamentals/](https://www.geeksforgeeks.org/computer-networks/open-shortest-path-first-ospf-protocol-fundamentals/)



The next questions are based on the following router network.  Each interface includes a network address and cost

<img src="https://champlain.instructure.com/courses/2682538/files/407188345/preview" alt="" height="280" width="600">

a.  (1) RIP is a distance-vector routing protocol.  It considers the number of hops to reach a destination and picks the shortest one.   Based on hop count. what is the shortest path between the client computer in the lower left and the server in Burlington, Vt and the number of hops. (**1 Point)**

* The shortest path is from the San Francisco Router -> Seattle - > Chicago -> Boston -> Burlington (5 hops)

b.  (2)OSPF is a cost-based protocol and determines the path with the least cost.  Based on cost, find the lowest-cost path between the client computer in the lower left and the server in Burlington, Vt. and what is the total cost of the route? (**1 Point)**

* The lowest cost path is San Fran (25) + Denver (25) + Kansas City (10) + New York (10) + Boston (10) + Burlington (50).
  * The total cost is 130.
