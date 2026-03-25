# Lab 12-1: Building a WLA

**Lab:**

1. Document your work in your Tech Journal taking meticulous notes of the\
   steps you take during the implementation of this lab. Words and pictures are\
   both good. Be sure to document any problems you had in the completion of\
   this lab as well as your successes.

| **Device** | **Interface** | **IP Address** | **Subnet Mask** | **Default Gateway** |
| ---------- | ------------- | -------------- | --------------- | ------------------- |
| Router     | Fa 0/0        | 192.168.30.1   | 255.255.255.0   | N/A                 |
| Router     | Fa 0/1        | 192.168.1.1    | 255.255.255.0   | N/A                 |
| Laptop1    | NIC           | DHCP           | 255.255.255.0   | 192.168.0.100       |

#### **Part 1: Configure a Wireless Router**

**Step 1: Configure the Internet connection type on the WR.**

1. Configure the Internet IP address according to the Addressing Table.
   1.

       <figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Screenshot of configured internet setup connections</p></figcaption></figure>

**Step 2: Configure the network setup.**

1. Scroll down to Network Setup. For the Router IP option, set the IP address to the Wireless Router’s LAN address and the subnet mask
2. Enable the DHCP server.
3. Scroll to the bottom of the page and click Save Settings.
   1.

       <figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Screenshot of configured DHCP server and internal network IP addresses</p></figcaption></figure>

**Step 3: Configure wireless access and security.**

1. At the top of the window, click Wireless. Set the Network Mode to Wireless-N Only and change the SSID to whatever you want to call your network.
2. Disable SSID Broadcast and click Save Settings.
   1.

       <figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Screenshot of Basic Wireless Settings</p></figcaption></figure>
3. Click the Wireless Security
4. Change the Security Mode from Disabled to WPA2 Personal.
5. Configure a passphrase.
6. Scroll to the bottom of the page and click Save Settings.
   1.

       <figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Screenshot of configured Wireless Security Settings (WPA2)</p></figcaption></figure>

#### **Part 2: Configure a Wireless Client**

**Step 1: Configure Laptop1  for wireless connectivity.**

Because SSID broadcast is disabled, you must manually configure Laptop1 with the correct SSID and passphrase to establish a connection with the router.

1. Click Laptop1 > Desktop > PC Wireless.
2. Click the Profiles
3. Click New.
4. Name the new profile Wireless Access.
5. On the next screen, click Advanced Setup. Leave on Infrastructure Mode. Then manually enter the SSID of your network on Wireless Network Name. Click Next.
6. Choose Obtain network settings automatically (DHCP) as the network settings, and then click Next.
7. On Wireless Security, choose WPA2-Personal as the method of encryption and click Next.
8. Enter the passphrase and click Next.
   1.

       <figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Screenshot of Confirm page for PC Wireless on L1</p></figcaption></figure>
9. Click Save and then click Connect to Network
   1.  .

       <figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Screenshot of successful wireless connection from L1 to Router</p></figcaption></figure>

**Step 2: Verify Laptop1 wireless connectivity and IP addressing configuration.**

1. The Signal Strength and Link Quality indicators should show that you have a strong signal.
2. Click More Information to see details of the connection, including IP addressing information. **SCREENSHOT #1**
   1.

       <figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption><p>Screenshot of wireless connection to router from L1</p></figcaption></figure>

**Step 3: Configure Laptops 2 and 3 to connect to Wireless**

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p>Screenshot of wireless connection to router from L2</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption><p>Screenshot of wireless connection to router from L3</p></figcaption></figure>

#### **Part 3: Connect to Wired Router and Web Server**

**Step 1: Configure the Wired Router with the correct IP addresses per the Table**

* Connect the Wired Router to the Wireless Router using a crossover cable and correct ports
* Connect the Wired Router to the Web Server using a crossover cable and the correct ports.

**Step 2: Access Web server from the Laptops**

* Using the Web Browser on the laptops – connect to the Web Server
* Show Laptop 2 connecting to Web Server. **SCREENSHOT #2**
  *

      <figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Screenshot of connection to server from L2</p></figcaption></figure>
* Show Laptop 3 connecting to Web Server. **SCREENSHOT #3**
  *

      <figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p>Screenshot of connection to server from L3</p></figcaption></figure>



## Setting up a Wireless Access Point

* WAN access
  * Click on the Router > GUI
  * Set Internet Connection Type to Static IP
    * Set the first IP address to your IP address
    * Set the default gateway to the INTERNET default gateway
* Internal network
  * Input the IP address into Network Setup and specify the subnet mask
  * Enable the DHCP server and set the IP address range
* Security
  * Select Wireless at the top > Basic Wireless Settings
    * Network Mode: Wireless-N Only
    * Network Name (SSID): TestNet
    * SSID Broadcast: Disabled
  * Select Wireless > Wireless Security
    * Select WPA2 Personal
    * Input passphrase of choice



(I didn't really have any issues with this lab :|)
