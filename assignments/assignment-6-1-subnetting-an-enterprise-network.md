# Assignment 6-1: Subnetting an Enterprise Network

Assignment 6-1: Subnetting Enterprise&#x20;

**Objectives:** Select and define appropriate subnet design for an organization to meet simple requirements

**Goals:**&#x20;

* Determine correct subnet mask given host requirements
* Determine correct network address
* Determine valid host ranges for subnets

&#x20;

**Assignment:**

## Skiff Co. is opening a new HQ in Burlington with the following Subnet Requirements

<img src="https://champlain.instructure.com/courses/2682538/files/407188409/download?wrap=1" alt="" height="401" width="435">

&#x20;

**Skiff Co. is using the 10.X.0.0/16 address space (where X is day in the month of your birthday (i.e. a number between 1 and 31)).**

&#x20;

**Create and complete a subnet table for the 5 subnets with the following headings (Columns):**

* **Subnet Name (e.g. Central Office, West Wing, Telecom VPN…)**
* **# of nodes/hosts required**
* **Network Address (e.g. 10.17.128.0)**
* **Subnet Mask (e.g. 255.255.254.0)**
* **Subnet Prefix (e.g. /23)**
* **First valid host IP address**
* **Last valid host IP address**



<table><thead><tr><th width="121.20001220703125">Subnet Name</th><th width="82.79998779296875"># Hosts Required</th><th width="106.00006103515625">Network Address</th><th>Subnet Mask</th><th>Prefix</th><th width="128">First Valid</th><th>Last Valid</th></tr></thead><tbody><tr><td>WiFi Network</td><td>1400</td><td>10.10.0.0</td><td>255.255.248.0</td><td>/21</td><td>10.10.0.1</td><td>10.10.7.254</td></tr><tr><td>Central Office</td><td>1100</td><td>10.10.8.0</td><td>255.255.248.0</td><td>/21</td><td>10.10.8.1</td><td>10.10.15.254</td></tr><tr><td>East Wing</td><td>615</td><td>10.10.16.0</td><td>255.255.252.0</td><td>/22</td><td>10.10.16.1</td><td>10.10.19.254</td></tr><tr><td>West Wing</td><td>550</td><td>10.10.20.0</td><td>255.255.252.0</td><td>/22</td><td>10.10.20.1</td><td>10.10.24.254</td></tr><tr><td>Telecommuter VPN Pool</td><td>100</td><td>10.10.25.0</td><td>255.255.255.128</td><td>/25</td><td>10.10.25.1</td><td>10.10.25.126</td></tr></tbody></table>
