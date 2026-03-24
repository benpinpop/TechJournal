# Lab 10-2: Observing ARP in Packet Tracer

## **Lab 10-2: ARP Packet Tracer Lab**

**Steps**

1. Start Packet Tracer and sign in with your Cisco Academy Credentials
2. Use the Devices Section in the lower left to build a simple network diagram using 4 generic computers and a switch
   * Select the Device Category, locate the device you want, and click-drag into the workspace
   * Do not connect the computers to the switch yet. (will embed graphic)
   * ![](https://champlain.instructure.com/courses/2616866/files/390785739/download?wrap=1)
3. Hold the mouse over each computer to see the configuration. Gather information about the devices and answer the following questions
   * ![](<../../.gitbook/assets/image (3).png>)
     * **Screenshot of PC0 configuration**
   * What is the MAC address of the ethernet adapter on PC0?
     * 0001.6493.0DC1
   * Is there an IP address?
     * There is no IP address.
   * Hold the mouse over the switch to see the configuration.
     *

         <figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>
   * Are there IP addresses assigned?
     * **There are no IP addresses assigned.**&#x20;
4. Click on PC0 - Desktop Tab
   * Open the Command Prompt&#x20;
   * Type arp  –a to  see the arp table and review to see if there are any entries
     *

         <figure><img src="../../.gitbook/assets/image (2) (1).png" alt="" width="345"><figcaption></figcaption></figure>

         There are no entries.&#x20;
5. Assign IP addresses to the computers (use 4 addresses on the same network : 10.10.10.X) What does it mean for PCs to be "on the same network"?
   * Select the computer, then Config tab, then FastEthernet0 ( Fa0)
   * Configure the IP addresses as follows.  Use a netmask of 255.255.255.0&#x20;
   * | PC | IP Address   |
     | -- | ------------ |
     | 0  | 10.10.10.100 |
     | 1  | 10.10.10.101 |
     | 2  | 10.10.10.102 |
     | 3  | 10.10.10.103 |
   * Review the ARP table entries of the PC's again
     * There are no still no ARP entries.&#x20;
6. Examine the address table of the switch. &#x20;
   * Click on the switch and the select CLI.   This is the Command Line Interface.   You need to get to the root CLI prompt which looks like **Switch#**
     * If the prompt looks like:  **Switch>,**  then type **enable** to enter admin mode
     * If the prompt looks like  **Switch (config)#**  type **exit** to get back to the basic mode for admin
   * Then type **show mac-address-table**
   * Review the table format for Mac Address and Port
     *

         <figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

         There are no MAC addresses inside the switch configuration.&#x20;
7. Use Ethernet cables to connect the computers to the switch.
   * The "Lightning Bolt" in the lower left will allow you to add connections between devices
   * Use the straight black cable (Ethernet straight-through) to connect PC0 to Fa0/10 on the switch, PC1 to Fa0/11...
   * ![](https://champlain.instructure.com/courses/2616866/files/390785715/download?wrap=1)
8. On PC0, open the Desktop and select Command Prompt.
9. From the command prompt on PC0, ping PC3 using it’s IP address.
10. **SUBMIT (2 Points) Screenshot showing successful ping between PC0 and PC3**
    1.

        <figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Successful ping from PC0 to PC3.</p></figcaption></figure>
11. Verify that all of the PC's can ping one another.  If not, troubleshoot and fix!
12. Now, inspect the configuration of the Switch using the steps outlined above in step 6 for the CLI and show mac-address-table.

    * **SUBMIT (3 Points):** Complete the following table&#x20;

    | MAC Address    | Port  |
    | -------------- | ----- |
    | 0001.6493.0dc1 | Fa0/1 |
    | 00e0.f94b.d91c | Fa0/2 |
    | 00d0.d320.ed9d | Fa0/3 |
    | 00e0.f795.6548 | Fa0/4 |



    *

        <figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Screenshot of <code>show mac-address-table</code> command on the switch</p></figcaption></figure>
13. **SUBMIT: Screenshot of Packet Tracer showing all 4 PC's connected to switch (1 Points)**
    1.

        <figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Screenshot of PCs connected to Switch</p></figcaption></figure>
