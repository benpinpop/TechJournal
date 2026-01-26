# Networking & Proxmox

## iptables

`iptables` is a Linux command-line tool that sets firewall and networking rules, like NAT. `iptables` handles not only incoming traffic but also outgoing traffic.&#x20;

There are a few important definitions to understand when looking at the iptables command.

* A **table** is the name for a set of chains
* A **chain** is a collection of rules stored within a table
* A **rule** is a condition used to match and identify packets&#x20;
* A **target** is an action when a rule matches, like accepting, dropping, or queueing the packet.&#x20;
* A **policy** is the default action taken when there is no rule match (ACCEPT or DROP)

The iptables command contains five accessible tables for network configuration:

| Table Name | Description                                                                                 |
| ---------- | ------------------------------------------------------------------------------------------- |
| filter     | Default used table for packet filtering. It includes chains like INPUT, OUTPUT and FORWARD. |
| **nat**    | Related to Network Address Translation. It includes PREROUTING and POSTROUTING chains.      |
| mangle     | For specialised packet alteration. Inbuilt chains include PREROUTING and OUTPUT.            |
| raw        | Configures exemptions from connection tracking. Built-in chains are PREROUTING and OUTPUT.  |
| security   | Used for Mandatory Access Control                                                           |

To&#x20;

## Resources and Articles

{% embed url="https://www.cloudflare.com/learning/dns/dns-server-types/" %}

{% embed url="https://learn.microsoft.com/en-us/training/modules/network-fundamentals/3-network-infrastructure" %}

{% embed url="https://learn.microsoft.com/en-us/training/browse/" %}

{% embed url="https://learn.microsoft.com/en-us/training/modules/introduction-to-powershell/5-exercise-cmdlets" %}
