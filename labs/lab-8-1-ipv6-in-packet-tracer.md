# Lab 8-1: IPv6 in Packet Tracer

## Commands

```bash
ipv6 unicast-routing # enable IPv6

int g0/0 # select the interfaces
int g0/1

ipv6 address [ADDRESS HERE] link-local # set the IPv6 address for local
ipv6 address [ADDRESS] # set IPv6 unicast
no shutdown # enable the interface
```

## Deliverables

**SUBMIT - Screenshot of PC1 command prompt successfully pinging the router on FE80::1 (2 Points)**

<figure><img src="../.gitbook/assets/image (142).png" alt=""><figcaption><p>Screenshot of a successful ping from PC1 to Router using IPv6</p></figcaption></figure>

**Screenshot of PC1 successfully pinging PC0 using the 2001:DB8:AAAA:A Address (1 point)**

<figure><img src="../.gitbook/assets/image (143).png" alt=""><figcaption><p>Screenshot of PC1 pinging PC0 using IPv6</p></figcaption></figure>

**Screenshot of PC1's auto-config IPV6 address on the 2001:DB8:AAAA:B network (1 point)**

<figure><img src="../.gitbook/assets/image (144).png" alt=""><figcaption><p>Screenshot of PC1's IPv6 Auto Configuration</p></figcaption></figure>

**Screenshot of PC0's auto-config IPV6 address on the 2001:DB8:AAAA:A network (1 point)**

<figure><img src="../.gitbook/assets/image (145).png" alt=""><figcaption><p>Screenshot of PC0's IPv6 Auto Configuration</p></figcaption></figure>
