# Lab 04b - Securing SSH on DHCP01

Allowing remote access to a known user account like Administrator or Root is a terrible idea! It allows an attacker to conduct an exhaustive attack using dictionaries of passwords against these known user accounts.

A security best practice is to disable Remote Access as root.

To disable root access, we go into the SSH config file in `/etc/ssh/sshd_config` and change `#permitrootlogon` to `no`

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
PermitRootLogon no
```
{% endcode %}

<figure><img src="../.gitbook/assets/image.png" alt="" width="340"><figcaption><p>Screenshot of a portion of the <code>sshd_config</code> file in <code>/etc/ssh/</code></p></figcaption></figure>

For our changes to take effect, we need to reload SSH, so we run the following command.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
sudo systemctl restart sshd
```
{% endcode %}

### /var/log/btmp Vs. journalctl -u sshd

