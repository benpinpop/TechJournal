# Lab 6.1: VLSM

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

### Background

PPC uses the private class B space of 172.16.0.0/16.  Currently all hosts are on the same network which is causing hate and discontent due to network performance impacts (hence, the sacking of Henry).  Here is some information which may help you in designing your subnet scheme.

### Mumbai Divisions

* Manufacturing will need 612 hosts
* Engineering will need 31 hosts

### North American Divisions

* Sales is the largest division with a host requirement of 1200
* HR needs 10 hosts &#x20;
* Accounting will need space for 24 hosts **(note gateways are part of this number too)**

&#x20;

1200=2^(32-x)-2

### Class Activity&#x20;

<table data-full-width="true"><thead><tr><th width="145">Name</th><th># Hosts</th><th width="150">CIDR</th><th>Network Address</th><th>First Usable Host Address</th><th>Last Usable Host Address</th><th>Broadcast Address</th><th data-hidden>Increment</th></tr></thead><tbody><tr><td>Sales (1200)</td><td>2048</td><td><p>172.16.0.0/21<br><br>172.16.0.0-172.16.7.255<br><br>21-16=5</p><p>2^5=32<br>32 subnets</p><p></p><p>256/32=8</p><p>Blocks of .8</p></td><td>172.16.0.0</td><td>172.16.0.1</td><td>172.16.7.254</td><td>172.16.7.255</td><td></td></tr><tr><td>Manufacturing (612)</td><td>1024</td><td>172.16.8.0/22<br><br>22-16=6<br>2^6=64<br>64 subnets<br><br>256/64=4<br>Blocks .4</td><td>172.16.8.0</td><td>172.16.8.1</td><td>172.16.11.254</td><td>172.16.11.255</td><td></td></tr><tr><td>Engineering (31)</td><td>64</td><td>172.16.12.0/26<br><br>26-24=2<br>2^2=4<br>4 subnets<br><br>256/4=64<br><br>Blocks of .0.64</td><td>172.16.12.0</td><td>172.16.12.1</td><td>172.16.12.62</td><td>172.16.12.63</td><td></td></tr><tr><td>Accounting (24)</td><td>32</td><td>172.16.12.64/27<br><br>27-24=3<br>2^3=8<br>8 subnets<br><br>256/8=32<br>Blocks of 0.32</td><td>172.16.12.64</td><td>172.16.12.65</td><td>172.16.12.94</td><td>172.16.12.95</td><td></td></tr><tr><td>HR (10)</td><td>16</td><td>172.16.12.96/28<br><br>28-24=4<br>2^4=16 subnets<br><br>256/16<br>Blocks of .16</td><td>172.16.12.96</td><td>172.16.12.97</td><td>172.16.12.110</td><td>172.16.12.111</td><td></td></tr><tr><td>Router Network (2?)</td><td>4</td><td>172.16.12.112/30<br><br>Blocks of .4</td><td>172.16.12.112</td><td>172.16.12.113</td><td>172.16.12.114</td><td>172.16.12.115</td><td></td></tr></tbody></table>

### Deliverable 2

Show successful pings to:

* Accounting First to Sales First
* Sales Last to Manufacturing Last
* HR First to Engineering First
* Engineering Last to Sales Last&#x20;
* HR Last to Accounting Last

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption><p>Successful pings from the indicated devices</p></figcaption></figure>

### Deliverable 3

<figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption><p>This screenshot shows my completed packet tracer file</p></figcaption></figure>

This lab was definitely a little difficult. I really struggled with the RIP routing, and understanding why ping wasn't working, but here are a few things that I've learned:

* The speed up button exists, so you don't have to wait for routers to turn back on and reinitialize
* Advertise all your networks via RIP routing, **ALL** of them
* Packet Tracer will yell at you when your subnet mask and IP address don't mix, and it is right most of the time
* Without a default gateway, a device cannot receive a ping
* Subnetting is easier than you think it is; it's just splitting up a network into logical pieces and then adding them on top of each other. Starting with bigger is better.&#x20;
* You have to turn on your router interfaces for them to work!<br>
