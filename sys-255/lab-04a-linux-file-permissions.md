# Lab 04a - Linux File Permissions

## Lab

_Create new users called Alice, Bob, and Charlie, and two new groups called Marketing and Management._

Alright, let's start by adding users using `useradd`, and creating a group with `groupadd`.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
useradd alice
useradd bob
useradd charlie

groupadd marketing
groupadd management
```
{% endcode %}

_Bob and Charlie should be in the Marketing group. Alice should be in the Management group._

We can add the specified users to the group using `usermod -aG [group] [user]`.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
usermod -aG marketing bob
usermod -aG marketing charlie
usermod -aG management alice
```
{% endcode %}

Great work! Let's create some directories.

_Create the directories /marketing and /management._

Use the `mkdir` command to create some directories.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
mkdir marketing
mkdir management

```
{% endcode %}

_Only the Marketing group should have the ability to view a file you create called /marketing/newproducts.txt_

To do this, we need to create a file and then change the group on the file. See below. Before we change file permissions, let's read the next instruction.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
echo "new product 1: automatic gold mining" >> newproducts.txt
chgrp marketing newproducts.txt
```
{% endcode %}

_Bob and Charlie should be able to see newproducts.txt, but only Bob should be able to modify the file_

We can change our file permissions using `chmod`, allowing us to only have Bob be able to modify the file, and Charlie can view it is as part of the marketing group.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
chmod 640 newproducts.txt 
# RW-   R--   ---
# Owner Group Other

chown bob newproducts.txt
```
{% endcode %}

_Alice is the manager. The new file, /management/bobreview.txt, should be modified only by Alice, and should be legible only by the Management group_

Okay, to do this, we need to repeat the same process as last time. We need to make Alice the owner, give her separate permissions, and we need to change the group of the file. Let's do it.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
echo "bob is doing okay" > /management/bobreview.txt
chgrp management bobreview.txt
chown alice bobreview.txt
chmod 640 bobreview.txt
```
{% endcode %}
