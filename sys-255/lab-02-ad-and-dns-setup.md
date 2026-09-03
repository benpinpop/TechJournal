---
description: Ben Polonsky
---

# Lab 02  - AD and DNS Setup

## Lab

### Set up AD01 Network Configuration

* IP Address: 10.0.5.5
* Subnet Mask: 255.255.255.0
* Gateway: 10.0.5.2
* DNS: 10.0.5.2

{% hint style="info" %}
Make sure to set the time zone to UTC-5:00 Eastern Time and change the hostname to `ad01-firstname`&#x20;
{% endhint %}

### Double Check your Networking

Run `ping google.com` and check your `hostname`.

### Setting up AD

* Click Manage in the Top Right > Add Roles and Features
* Select Active Directory Domain Services -> Add Features
* Choose the "Restart Destination Server" option, and select Yes on Confirmation
* Close the menu once installed.&#x20;
* Look at the top right and click "Promote this server to a domain controller"

### Deployment Configuration

* Add a new forest > ben.local
* Enter a DSRM password
* Ignore the DNS error.
* Reboot!
* Login as your domain administrator, it should look like BEN\Administrator

### DNS Configuration

* Your Preferred DNS is now 127.0.0.1. Your domain controller now serves as the DNS server for your entire domain. When it fails it will go to your gateway. Hooray!
* Go to your Server Manager > DNS
* Right-click on the AD01-BENP entry in the SERVERS list. > DNS Manager
* Navigate to ad01-benp.ben.local > Forward Lookup Zones
  * Right-click on the folder or click Action, then click New Host (A or AAAA)...
    * Enter ad01-benp, IP: 10.0.5.5
    * Enter fw01-benp, IP: 10.0.5.2
  * Click Update associated PTR record!
* To resolve an **hostname by an IP address** you need to create a **Reverse Lookup Zone**.
  * &#x20;Go back into your DNS Manager > ad01-benp.ben.local >Reverse Lookup Zones
  * Right click on Reverse Lookup Zones and click New Zone...
  * Set the Network ID to 10.0.5
  * Create PTR records for ad01 and fw01 by unchecking and updating the associated PTR record in the Forward Lookup Zones

### Creating AD Users

* Go to Server Manager > AD DS
* Right-click on the AD01-BEN server > Active Directory Users and Computers
* Navigate to ben.local > Users, right click or click action
* Click New > User
  * Fill in the infromation, and click Add to a group
  * Add object: "Domain Admins"
* Create a non-priveleged account as well.

### Joining a computer to a domain

* Go to network configuration and change the DNS server 10.0.5.5, which is the domain controller.
  * The domain controller NEEDS to be the DNS server.
* After setting your DNS server to 10.0.5.5, you should be able to ping fw01-benp.ben.local and ad01-benp.ben.local, as well as nslookup 10.0.5.5 and 10.0.5.2.
  * If you can't, you did something wrong!
* Go to your Settings > About > Advanced System Settings
  * You should now be in the System Properties Window
* Click Change... under the Computer Name tab.
* Click Member of... > Domain: `ben`
* Click _Ok_, a username and password prompt should show up.&#x20;
* Use your domain admin password to join the computer to the domain, this may take some time.
* You did it! Hooray!
* Go back into your Active Directory Users and Computers App under AD DS > AD01 Server.
  * Go to Computers, you should see WKS01-BEN









