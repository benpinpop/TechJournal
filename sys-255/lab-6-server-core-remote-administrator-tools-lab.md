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

