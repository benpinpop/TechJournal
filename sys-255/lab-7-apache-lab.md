# Lab 7 - Apache Lab

## Lab

### Network The Box

* Change the cable
* Set IP via NMTUI to 10.0.5.10
* Change the hostname to web01-ben

### Create your Sudo User

{% code title="CLI" overflow="wrap" lineNumbers="true" expandable="true" %}
```
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
```
dnf install -y bind-utils
```
{% endcode %}

### Opening the Firewall

We need to use firewall-cmd to open http and https.

{% code title="CLI" overflow="wrap" lineNumbers="true" expandable="true" %}
```
firewall-cmd --permanent --add-service=http
firewall-cmd --permanent --add-service=https
firewall-cmd --reload
```
{% endcode %}

### Installing httpd

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
dnf install httpd
systemctl enable httpd
systemctl start httpd
```
{% endcode %}

### Add DNS Records to AD

Go to your Server Manager and add DNS records for web01-ben and map it to 10.0.5.10. Make sure to add a PTR record.

### Yeet the welcome.conf file and make your own index.html

Delete `/etc/httpd/conf.d/welcome.conf` and create an `index.html` file using nano.

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
nano /var/www/html/index
```
{% endcode %}

### Install PHP and make a PHP page

To add dynamic content to your web page. Install PHP using the following:

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
dnf install -y php
```
{% endcode %}

