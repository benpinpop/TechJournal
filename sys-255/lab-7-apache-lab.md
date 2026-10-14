# Lab 7 - Apache Lab

## Lab

### Network The Box

* Change the cable
* Set the IP via NMTUI to 10.0.5.10
* Change the hostname to web01-ben

### Create your Sudo User

{% code title="CLI" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
adduser ben
passwd ben # Set the password for Ben
usermod -aG wheel ben
```
{% endcode %}

### Disable Root SSH

Edit `/etc/ssh/sshd_config` and modify the line to disable PermitRootLogin.

{% code title="/etc/ssh/sshd_config" overflow="wrap" lineNumbers="true" expandable="true" %}
```
PermitRootLogin no
```
{% endcode %}

Restart sshd by running `systemctl restart ssh` or `systemctl restart sshd` depending on the system.

### Install nslookup using dnf

To install nslookup, you need bind-utils. Install with:

{% code title="CLI" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
dnf install -y bind-utils
```
{% endcode %}

### Installing HTTPD and Opening the Firewall&#x20;

First you use dnf to install httpd, systemctl to enable and start, and firewall-cmd to open http and https.

{% code title="CLI" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
dnf install httpd
systemctl enable httpd
systemctl start httpd

firewall-cmd --permanent --add-service=http
firewall-cmd --permanent --add-service=https
firewall-cmd --reload
```
{% endcode %}

### Add DNS Records to AD

Go to your Server Manager and add DNS records for web01-ben and map it to 10.0.5.10. Make sure to add a PTR record.

### Yeet the welcome.conf file and make your own index.html

Delete `/etc/httpd/conf.d/welcome.conf` and create an `index.html` file using nano.

{% code title="CLI" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
nano /var/www/html/index
```
{% endcode %}

### Install PHP and make a PHP page

To add dynamic content to your web page. Install PHP using the following:

{% code title="CLI" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
dnf install -y php

# Now adding a PHP page
nano /var/www/html/index.php
```
{% endcode %}

{% code title="/var/www/html/index.php" overflow="wrap" lineNumbers="true" expandable="true" %}
```php
<?php echo "HELLO SYS255</br>"; 
for ($x=1; $x <= 10; $x++) {
    echo "X is now: $x</br>";
}
?>
```
{% endcode %}

### Domain joining from Linux

First, install your dependencies.

{% code title="CLI" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
dnf install -y realmd samba samba-common oddjob oddjob-mkhomedir sssd adcli

realm join --user=ben-adm@BEN.LOCAL BEN.LOCAL
# You'll be prompted for a domain password.
```
{% endcode %}

You should now be domain joined!
