# Lab 6 - Server Core / Remote Administrator Tools Lab

## Goals

The goal of this lab is to set up a file share server and set up permissions using GPOs. Below is the executive summary of how to set up and complete this lab.

## Current Network

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
FW02-BEN: 10.0.5.2
AD02-BEN: 10.0.5.6
DHCP02-BEN 10.0.5.33
WKS02-BEN: DHCP
FS01-BEN: 10.0.5.8
```
{% endcode %}

## Lab

### Setting up FS01

* Log into FS01. You'll be prompted to change the administrator password.
* Use Option 1 in the Server Config Panel to join the domain to ben.
  * You'll be prompted for a domain admin user and password.
  * Say _Yes_ when it asks you to change the hostname, and name it `FS01-BEN`
* After restarting, you need to change your network settings using Option 8.&#x20;
  * Set the IP address to: `10.0.5.8`
  * Set the Subnet Mask to: `255.255.255.0`
  * Set the Default Gateway to: `10.0.5.2`
* Once complete, make sure to set the DNS to `10.0.5.6` otherwise your AD won't work. :(

{% hint style="danger" %}
Not able to join your domain? You are probably cabled to WAN, and not your SYS-255 LAN! Cable your VM!
{% endhint %}

### Installing RSAT onto AD02

* Go to Server Manager
* Go to the top right of Server Manager > Manage > Add Roles and Features
* Select the following options
  *

      <img src="../.gitbook/assets/unknown (98).png" alt="Add Roles and Features Wizard > Features Menu" height="381" width="432">


* Install.

### Add DNS for FS01 and add FS01 to Server List

* Go to Server Manager > DNS. Click on AD02 and open up the DNS Manager.
* Add FS01-BEN to the DNS Manager using IP address `10.0.5.8`.&#x20;
* Make sure there is a PTR record as well.
* Go back to the top right of Server Manager > Manage. Click on Add Servers and add FS01-BEN
  *

      <img src="../.gitbook/assets/unknown (99).png" alt="Example of what your menu should look like." height="283" width="624">


* Refresh the Server List.

### Setting up our OUs again

* Go back to Server Manager and go to AD02, or click on Tools > Active Directory Users and Computers.
* Create new Organizational Units. At the end, it should look like this:

<img src="../.gitbook/assets/unknown (100).png" alt="Example of Organizational Unit Structure" height="320" width="406">

* Create a new Global security group (Sales-Users) in the Groups OU.
* Create two users (Bob and Alice) as standard domain users, in the new SYS255\Users OU
* Add Alice to the Sales-Users group

### Add FSRM to FS01-BEN

* Go to FS01 in Server Manager. Right-click and click Add Server Roles and Features.
  *

      <img src="../.gitbook/assets/unknown (101).png" alt="" height="402" width="431">
* Install.&#x20;

### Modifying Firewall Rules on FS01

Input this command into your terminal on FS01 after installing the Firewall Server Resource Manager.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
netsh advfirewall firewall set rule group=”Remote File Server Resource Manager Management” new enable=yes
```
{% endcode %}

{% hint style="warning" %}
If you encounter an error when changing the firewall rules, try reinstalling the File Server Resource Manager
{% endhint %}

### Adding File Shares via AD02

* Go back to your Server Manager. Click on the File and Storage Services

<figure><img src="../.gitbook/assets/image (141).png" alt="" width="176"><figcaption><p>What your Server Manager Tab should look like</p></figcaption></figure>

* Create a new share.
  *

      <img src="../.gitbook/assets/unknown (102).png" alt="What your Shares should look like" height="351" width="624">
* Choose the SMB Quick Share option and select FS01.
* Name the Share Sales.
* Click on the Sales Share, right click, and select _Properties_.
* Remove access for Everyone and change the principal to Sales-Users group that we made before. Now only the Sales-Users will have access to this file share.

{% hint style="info" %}
Make sure to test by logging in on WKS01 as Alice and Bob.
{% endhint %}

### Adding a network map via Group Policy Object

* Go to Tools and click on Group Policy Management Console or right-click on the AD02 server and click on Group Policy Management Console
* Add a new GPO to SYS255 > Users and name it Sales-Drive
* Right click on the GPO and click _Edit..._
* Open User Configuration > Preferences > Windows Settings > Drive Maps
* Right-click on Drive Maps and create New > Mapped Drive.
  * Location: \\\FS01-BEN\Sales
  * Label as: Sales-User-Drive
  * Select _Show This Drive_
* Apply your changes.
* Go into common and select Item-based targeting, and open up the targeting menu.
* Add a new item that specifies that the security group must be a part of the Sales-Drive security group.
