# Lab 04a - Linux File Permissions

## Lab

_Create new users called Alice, Bob, and Charlie, and two new groups called Marketing and Management._

Alright, let's start by adding users using `useradd`, and creating a group with `groupadd`.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
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
```
usermod -aG marketing bob
usermod -aG marketing charlie
usermod -aG management alice
```
{% endcode %}

Great work! Let's create some directories.

_Create the directories /marketing and /management._

Use the `mkdir` command to create some directories.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
mkdir marketing
mkdir management

```
{% endcode %}

1. _Only the Marketing group should have the ability to view a file you create called /marketing/newproducts.txt_



1. _Bob and Charlie should be able to see newproducts.txt, but only Bob should be able to modify the file_



1. _Alice is the manager. The new file, /management/bobreview.txt, should be modified only by Alice, and should be legible only by the Management group_
