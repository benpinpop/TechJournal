# Lab 3-2: MAC OUI and MAC Spoofing Lab

**MAC OUI and MAC Spoofing Lab**

Objective:

Understand the Organization Unit Identifier in a MAC address and observe the potential of MAC address spoofing

Goals:

* Identify and decode the MAC address OUI
* Use a MAC changing tool to spoof a MAC address

**Part 1- Organization Unit Identifier (OUI): 2 Points**

The OUI:

* The first 24 bits of a **MAC address** for a network-connected device, which indicate the specific vendor for that device.
* The IEEE assigns OUIs to vendors
* OUI Lookup Site:
  * [httpsLinks to an external site.](https://www.wireshark.org/tools/oui-lookup.html)[://Links to an external site.](https://www.wireshark.org/tools/oui-lookup.html)[www.wireshark.org/tools/oui-lookup.htmlLinks to an external site.](https://www.wireshark.org/tools/oui-lookup.html)
* Remember: second 24 bits of MAC is the unique serial assigned to the device by the manufacturer

Lab Steps

1. From the Kali VM lookup your Default Gateway (ip route show)  and make a note of it.
2. Start a Wireshark capture
3. Ping the Default Gateway
4. Stop the capture
5. Analyze the capture and use the OUI lookup tool at [httpsLinks to an external site.](https://www.wireshark.org/tools/oui-lookup.html)[://Links to an external site.](https://www.wireshark.org/tools/oui-lookup.html)[www.wireshark.org/tools/oui-lookup.htmlLinks to an external site.](https://www.wireshark.org/tools/oui-lookup.html) to submit the following:
   * **SUBMIT: The OUI number and vendor info for the Default Gateway**

**Part 2: MAC Spoofing (2 Points)**

MAC addresses are often called the “burned in address”. NIC manufactures will assign MAC address to the device and is traditionally stored in a ROM chip and preloaded into non-volatile memory.&#x20;

However, NICs such as some using USB or created by Virtual Machines, do not have the MAC address preloaded in firmware and rely on software drivers to assign the MAC.  Therefore, it is possible on many systems to "change" the MAC address as used by the O.S.

This can be demonstrated through a tool like MACChanger for Kali.

Lab Steps:

1. Bring up your Kali VM.
2. Open a terminal
3. Type the following to see info on the macchanger command-line tool
   * macchanger --help
4. Type the following command to show the current/permanent MAC address
   * macchanger -s eth0
5. Use the OUI Database List at [https://code.wireshark.org/tools/oui-lookup.htmlLinks to an external site.](https://www.wireshark.org/tools/oui-lookup.html)
   * Find an OUI for an older gaming console (Atari, Intellivision, Commodore, Sega...)
   * Can use the Find feature in your browser
6. Change your mac address on the Kali box to:
   * The OUI for a game console from step 5
   * and the serial # de:fa:ce
   * using the command
     * sudo macchanger -m xx:xx:xx:de:fa:ce eth0
     * where xx:xx:xx is the spoofed OUI
     * "sudo" is required to obtain the administrator privileges needed to change the MAC. When prompted, enter "kali" as your password.
7. You should see that the MAC has changed
8. Start a Wireshark capture on your Kali VM for interface eth0
9. Ping 8.8.8.8 (in linux the default is to ping forever. You can hit Ctrl-C in the terminal to stop the pings.)
10. Stop capture
11. **SUBMIT: Screenshot of ping request that shows your spoofed MAC address in the Ethernet header**
