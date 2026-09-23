# Lab 5 - AD DS GPO Lab

## Lab

### Creating Organizational Units (OUs)

Go to _Server Manager,_ in the top right, and click _Tools > Active Directory Users and Computers_.

<img src="../.gitbook/assets/unknown (93).png" alt="Screenshot for Jeastman&#x27;s Lab" height="190" width="684">

All we need to do is right-click on any the ben.local object, click _New > Organizational Unit,_ and name our OU. We want the structure to look like this:

<img src="../.gitbook/assets/unknown (94).png" alt="Screenshot from Jeastman&#x27;s Lab of Actsersive Directory Users and Computers" height="345" width="438">

### Creating Users and Groups, and adding Computers

Right click the Accounts folder, and click _New > Users_. Name the user accordingly, and uncheck _Reset Password on Login_. The accounts should look something like this:

<figure><img src="../.gitbook/assets/image (133).png" alt=""><figcaption></figcaption></figure>

To add a computer to our computer folder, all we need to do is go to _ben.local > Computers_, and drag the WKS01 Computer to the _ben.local > SYS255 > Computers_ OU. Finally, to create a group, we click on Groups and click _New > Group._ We want it to be a Global Security Group with Alice and Bob, but not Charlie. See the photo below:

<img src="../.gitbook/assets/unknown (96).png" alt="" height="377" width="439">

Double click on the Object and go to Members. Click Add... and add aliceLab5 and charlieLab5.

{% hint style="info" %}
Too busy ricing your Windows machine? Lock in.
{% endhint %}

### Creating a new Group Policy

Go to the _Server Manager_ and go to the top right to _Tools > Group Policy Management._ Open up your forest and go down to _SYS255_ and right click and add a new Group GPO, it should be the first item on the menu. Click on the GPO to see its settings.

<img src="../.gitbook/assets/unknown (97).png" alt="" height="245" width="474">

Go to the Security Filter, and add custom-desktop, and remove Authenticated Users. Add _Domain Computers_ to the Security Filter list. Go to Delegation (on the top) > Advanced... Click on Domain Computers, and click _Deny_ on the _Apply Group Policy_ setting.

### Editing a Group Policy

Right-click on the new Group Policy and click _Edit..._ From there, we can apply any settings we want to disable the Recycling Bin.

<img src="../.gitbook/assets/unknown.png" alt="Screenshot of the directories to enable the setting that removes the recycling bin icon from the desktop" height="315" width="624">

If we want to disable the last logon, all we need to do is disable the setting using a group policy:

<img src="../.gitbook/assets/unknown (1).png" alt="" height="332" width="624">

### Commands to know

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
gpresult /r 
gpupdate /force
gpresult /scope computer /r
```
{% endcode %}

## Guide for Assessment Prep

Snapshot back to base and rebuild it from scratch! Also, try to rebuild the environment in my own Proxmox Server, and time how long it takes to rebuild everything. YAYYYYY.

### Network Map

<figure><img src="../.gitbook/assets/Untitled Diagram.drawio.png" alt=""><figcaption><p>Network Diagram!!!!</p></figcaption></figure>

