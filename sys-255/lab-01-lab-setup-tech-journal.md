# Lab 01 - Lab Setup Tech Journal

## Setup Info

### Gateway/Router Info

| Title            | IP address     |
| ---------------- | -------------- |
| WAN Address      | 10.0.17.104/24 |
| Upstream Gateway | 10.0.17.2/24   |
| LAN Gateway      | 10.0.5.2/24    |
| wks01            | 10.0.5.100     |

### Network Map

<img src="../.gitbook/assets/unknown (85).png" alt="Network Map of the cyber.local proxmox" height="536" width="624">

### [Default Passwords](https://docs.google.com/document/d/1soobnhDH-X-YoE_9hC3bEfEz4P3C4axshACcp55AwjY/edit?usp=sharing)

| System                 | Username                             | Password     | Notes                             |
| ---------------------- | ------------------------------------ | ------------ | --------------------------------- |
| Rocky VMs              | root                                 | Ch@mpl@1n!26 | <p><br></p>                       |
| Rocky VMs \[Alternate] | <p>champuser</p><p> (if present)</p> | Ch@mpl@1n!26 | <p><br></p>                       |
| Xubuntu VMs            | champuser                            | Ch@mpl@1n!26 | <p><br></p>                       |
| Ubuntu Servers         | champuser                            | Ch@mpl@1n!26 | <p><br></p>                       |
| OPNsense               | root                                 | Ch@mpl@1n!26 | <p><br></p>                       |
| pfSense                | admin                                | pfsense      | <p><br></p>                       |
| Windows 11             | champuser                            | Ch@mpl@1n!26 | <p><br></p>                       |
| Server 2022            | Administrator                        | Ch@mpl@1n!26 | Password Change Occurs Upon Login |
| VyOS                   | vyos                                 | Ch@mpl@1n!26 | <p><br></p>                       |
| Kali Linux             | champuser                            | Ch@mpl@1n!26 | <p><br></p>                       |

## Lab

### Step 1 - Setting up Network Devices

Select your VM > Hardware. Then select your network device and double-click or click _Edit_.

<figure><img src="../.gitbook/assets/image (93).png" alt=""><figcaption><p>Screenshot of the Hardware menu of fw01 VM</p></figcaption></figure>

Select the Bridge of your choice (WAN or LAN) and use either VirtIO or E1000. **For this lab, net0 is SYS01013 (WAN) and net1 is SYS01029 (LAN).**

<figure><img src="../.gitbook/assets/image (94).png" alt=""><figcaption><p>Screenshot of the network device menu of fw01 net0</p></figcaption></figure>

Click _OK_ to finalize any changes. You may need to restart your VM.

### Step 2 - Navigate to the pfSense console and assign network interfaces

Click on the VM > Console or double-click on the VM icon to open up a full-screen window. From there, you should see a window that looks something like this. (You may need to log in.)

<figure><img src="../.gitbook/assets/image (95).png" alt=""><figcaption><p>pfSense 2.7.2 home screen in fw01</p></figcaption></figure>

To assign your interfaces, input _1_ into the option menu. Ensure vtnet0 is set to WAN and vtnet1 is set to LAN. Do not set up VLANs. Input _y_ to proceed with changes.

From there, you will need to assign your IP addresses. Input _2_ into the option menu. You will need to repeat this process for each network interface. Set the WAN IP address and Upstream Gateway. Set the LAN IP address; do NOT add a gateway. The LAN IP address serves as the gateway.&#x20;

{% hint style="danger" %}
Do NOT enable DHCP. Do NOT add a gateway for LAN. Do NOT configure IPv6, you're not good enough for that yet.
{% endhint %}

### Before you leave pfSense

Important Options to remember:

* Reset web console password - 3
* Reset to factory default - 4
* Reboot - 5
* Ping hosts - 7
* Shell - 8
* Restart web console - 11

{% hint style="info" %}
The password for the pfSense web panel is `admin - pfsense`
{% endhint %}

### Step 3 - Reassign the Network Device for wks01

Repeat the process from Step 1 on wks01 and assign net0 to **LAN**.&#x20;

### Step 4 - Change the Hostname - Windows

To rename your computer, enter the Search bar in Windows and look up _rename_; select the option _View your PC name._ Alternatively, go to Windows Settings > About.

<figure><img src="../.gitbook/assets/image (96).png" alt=""><figcaption><p>Windows Search Menu for <em>rename</em></p></figcaption></figure>

Upon arriving at the About screen, click on _Rename this PC_. From there, you will be prompted to rename the computer.&#x20;

{% hint style="info" %}
The format is `wks01-yourfirstname`
{% endhint %}

### Step 5 - Setting up a new local account

Congratulations, you've logged in! Now you need to make a new account. Open up Run with _Windows + R_ or search _Run._ Enter _lusrmgr.msc,_ and you should open up the User Manager. Click on the Users Folder, and select Action.

<figure><img src="../.gitbook/assets/image (97).png" alt=""><figcaption><p>Action Menu in <em>lusrmgr.msc</em></p></figcaption></figure>

Input the full User Name and Password, which obviously should be the same as the default one so someone can hack your box. Do not require the user to change the password at the next logon.

So how do you give it admin permissions? Great question. Go to the Groups folder in the left-hand column. Double-click on the _Administrators_ group, click _Add..._ and input the exact name of your user. Windows is picky. Great work, now your user has admin permissions.&#x20;

<figure><img src="../.gitbook/assets/image (98).png" alt=""><figcaption><p>Screenshot of our champuser in the Administrators group</p></figcaption></figure>

### Basic Commands in Command Prompt

Now log in as your user and open up the Command Prompt. The whoami command will output the hostname concatenated with the current user.

<figure><img src="../.gitbook/assets/image (99).png" alt=""><figcaption><p><code>whoami</code> in Command Prompt</p></figcaption></figure>

The hostname command will only output the hostname. Shocker.

<figure><img src="../.gitbook/assets/image (100).png" alt=""><figcaption><p><code>hostname</code> comamnd in Command Prompt</p></figcaption></figure>

### Step 6 - Setting up the Network

Click on the little Ethernet button on the bottom right, and select the Network.

<figure><img src="../.gitbook/assets/image (101).png" alt=""><figcaption><p>Screenshot of the Windows Network Panel</p></figcaption></figure>

{% hint style="warning" %}
If you have no Network, you messed up Step 3. Go back, fix it, and restart your VM. <sub>If that still doesn't work, set the VM on fire.</sub>
{% endhint %}

This should open the Ethernet menu. Click on the only connected network and scroll down to _IP settings_. Click _Edit_.&#x20;

* Set it to Manual, not DHCP
* Turn on IPv4
* Input the following settings.

<figure><img src="../.gitbook/assets/image (102).png" alt=""><figcaption><p>Custom IP Configuration for wks01</p></figcaption></figure>

Great work, you should now have internet. Open up the command prompt, and you should be able to ping 10.0.5.2 and 10.0.17.2.

<figure><img src="../.gitbook/assets/image (103).png" alt=""><figcaption><p>Successful pings of 10.0.5.2 and 10.0.17.2 in Command Prompt in wks01</p></figcaption></figure>

Now try pinging 8.8.8.8. That doesn't work? Wow... Um.. Try again?

<figure><img src="../.gitbook/assets/image (105).png" alt=""><figcaption><p>This is what we call a Cyber Admin issue...</p></figcaption></figure>

Now try resetting your configuration and repeating the process all over again in hopes that you can ping 8.8.8.8 or 1.1.1.1. Funny, it only works half the time! Okay, welp, time to set up the actual pfSense web portal!

### Step 7 - Setting up pfSense via HTTPS

Navigate to https://10.0.5.2/. This is the IP address of the pfSense box, and should have the webConfigurator portal running.

{% hint style="info" %}
Not working? Are you sure you typed `https` instead of `http`? Still not working, try pinging 10.0.5.2. No ping? Re-check your pfSense interfaces, and then your Windows network configuration.
{% endhint %}

You should arrive at a page that looks a little like this. If you encounter a certificate warning screen, ignore that, you're totally getting hacked anyway. Log in with the credentials: `admin - pfsense`

<figure><img src="../.gitbook/assets/image (106).png" alt=""><figcaption><p>pfSense login page</p></figcaption></figure>

{% hint style="warning" %}
Do not use Internet Explorer. You will not be able to log in; it does not like redirects.
{% endhint %}

From there, USE the wizard. Set the following information: Skip through everything else.

* Hostname: fw1-benp
* Domain: benp.local
* Primary DNS: 8.8.8.8 or 1.1.1.1, backup DNS can be either or.
* System Wizard:  Configure WAN Interface
  * SET THE DEFAULT GATEWAY (10.0.17.2)
* RFC1918 Networks:  Uncheck "Block private networks from entering via WAN"

Great, you're all good to go. Now let's ping the internet and get DNS resolution!&#x20;

## Deliverables

**Deliverable 1:  Screenshot showing a successful ping from fw01 to champlain.edu:  Select 8 to get a shell, and then execute the ping shown below.  Type exit to leave the command shell.(3 points)**

<img src="../.gitbook/assets/unknown (86).png" alt="This first screenshot shows the fw1-benp box terminal. In this screenshot, I entered option 8, which sends the option screen to a shell. In that shell, I attempted to ping champlain.edu, but forgot to put a number for the count option. I then pinged champlain.edu. The screenshot shows that 1 packet was transmitted and received, meaning it was a successful ping." height="349" width="624">

<img src="../.gitbook/assets/unknown (87).png" alt="In this screenshot, I entered the exit command to exit to the option menu in the fw1 pfSense box." height="329" width="624">

**Deliverable 2: On wks01, figure out how to invoke powershell and provide a screenshot similar to the one below showing the output of the following commands:  whoami, hostname, ping -n 1 google.com and ipconfig (2 points)**

<img src="../.gitbook/assets/unknown (88).png" alt="This screenshot shows the wks01 (in a box in green on the left) PowerShell terminal. In this terminal, the command whoami was run, which displays “wks01-benp/champuser.” Champuser was not the default user (only Administrator existed, so I logged in via champuser. The hostname was run, which displays the computer hostname “wks01-benp.” After running the hostname command, the ping command was used to ping Google once with one ICMP packet (-n 1). The result of the command is a successful ping (Sent = 1, Received = 1, Lost = 0). After running the ping command, the ipconfig command is ran (ipconfig /all), which displays the computer’s network configuration. Only one Ethernet adapter is configured according to the screenshot." height="295" width="624">

**Deliverable 3:  Take a screenshot showing successful navigation from wks01 to champlain.edu using chrome.  Make sure to get the Virtual Machine Name VM window banner (2 points)**

<img src="../.gitbook/assets/unknown (89).png" alt="In this screenshot, the wks01 box is opening the champlain.edu page in Microsoft Edge. Highlighted in a green box is the Champlain logo and the Virtual Machine Name. " height="285" width="624">

**Deliverable 4: On wks01, use the tracert command against champlain.edu with a maximum of three hops.  This command should illustrate how packets are being routed from your private LAN to your WAN. Provide a screenshot showing your tracert command and hops 1-3. (1 point)**

<img src="../.gitbook/assets/unknown (90).png" alt="This screenshot shows the tracert command being run in the wks01 box on champlain.edu. The first hop is 10.0.5.2, which is the LAN Gateway. The second hop is 10.0.17.2, which is the upstream gateway. The third hop is 192.168.4.252, the final gateway before the internet, according to the network map." height="360" width="624">

**Deliverable 5:  Consider this lab.  What technical terms or steps were you unfamiliar with?  Provide at least 3 examples (1 point).  Example:**

| I was definitely unfamiliar with the WAN and LAN setup. I know the terms and how they work functionally, but getting them through my head was a little difficult, same with the PfSense Setup.              |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| The lab mentioned that we shouldn’t enable DHCP, why not? Isn’t the PfSense VM capable of using DHCP?                                                                                                       |
| I was not very familiar with the steps to set up the PfSense box, or the proper/correct subnet mask on the Windows box. There’s no guidance in the input (but I totally should have read the instructions). |

## Issues and Difficulties

Pinging 8.8.8.8 really only works half the time, and my DNS works even less than half the time. Traceroute shows the packets going all the way up to 10.0.17.2, and dropping either at the upstream gateway or at the gateway after that.&#x20;

<figure><img src="../.gitbook/assets/image (107).png" alt=""><figcaption><p>ping and tracert to 8.8.8.8 from wks01</p></figcaption></figure>

I honestly have no clue anymore. I do need help with this! Two seconds later, it works perfectly fine!

<figure><img src="../.gitbook/assets/image (108).png" alt=""><figcaption></figcaption></figure>
