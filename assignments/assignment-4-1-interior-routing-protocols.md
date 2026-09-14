# Assignment 4-1: Interior Routing Protocols

**Interior Routing Assignment**

**Routing Information Protocol v2 (RIP v2)**

Do some research into RIPv2 and review the protocol header information to answer the following questions (**make sure to include citations!**)

RIPv2 Fields

1. The job of any routing protocol is to provide a mechanism for exchanging information about routes so routers can keep their routing tables up-to-date. Describe in your own words (a few sentences and/or detailed bullet points) the mechanism RIP uses so that routers in a network can build their routing table. **(2 Points)**
2. Describe in your own words, how RIP uses the Route Distance Metric (**1 Point)**
3. Describe in your own words (a few sentences or detailed bullet points) the limitations of RIP on a larger network **(2 Points)**

&#x20;

**Open-Shortest Path First (OSPF)**

OSPF is a very popular interior routing protocol and is widely used in larger enterprises.

1. Describe in your own words (a few sentences and/or detailed bullet points) the mechanism OSPF uses so that routers in a network can build their routing table and how it differs from RIP v2. **(2 Points)**
2. Describe in your own words, how OSPF uses the "Cost" Metric (**1 Point)**

&#x20;

The next questions are based on the following router network.  Each interface includes a network address and cost

<img src="https://champlain.instructure.com/courses/2682538/files/407188345/preview" alt="" height="280" width="600">

a.  (1) RIP is a vector distance router protocol.  It considers the number of hops to reach a destination and picks the shortest one.   Based on hop count. what is the shortest path between the client computer in the lower left and the server in Burlington, Vt and the number of hops. (**1 Point)**

* The shortest path is from the San Francisco Router -> Seattle - > Chicago -> Boston -> Burlington (5 hops)

b.  (2)OSPF is a cost-based protocol and determines the path with the least cost.  Based on cost, find the  lowest cost path between the client computer in the lower left and the server in Burlington, Vt. and  what is the total cost of the route? (**1 Point)**

* The lowest cost path is San Fran (25) + Denver (25) + Kansas City (10) + New York (10) + Boston (10) + Burlington (50).
  * The total cost is 130.
