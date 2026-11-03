# CMS Assessment Rehearsal

## Current Network

```
FW02-BEN: 10.0.5.2
AD02-BEN: 10.0.5.6
DHCP02-BEN 10.0.5.33
WKS02-BEN: DHCP
FS01-BEN: 10.0.5.8
```

## Deliverables

* Change hostname (web01-ben) - `nmtui`
* Change IP address to 10.0.5.11 - `nmtui`
* Domain Join - See [#domain-joining](cms-assessment-rehearsal.md#domain-joining "mention")
* Install a CMS/Blogging Software

## Domain Joining

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
dnf install -y realmd samba samba-common oddjob oddjob-mkhomedir sssd adcli

realm join --user=ben-adm@BEN.LOCAL BEN.LOCAL
# You'll be prompted for a domain password.
```
{% endcode %}

## Adding a user

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
adduser ben
passwd ben # Set Passwd

sudo usermod -aG wheel ben
```
{% endcode %}

## Installing HTTPD

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```bash
dnf update -y
dnf install -y httpd unzip curl
dnf install -y php php-cli php-gd php-mbstring php-xml php-json php-curl php-zip

systemctl enable --now httpd
firewall-cmd --permanent --add-service=http
firewall-cmd --reload

cd /tmp
curl -L -o bludit.zip https://www.bludit.com/releases/bludit-latest.zip
unzip bludit.zip
mv bludit-* /var/www/html/bludit

chown -R apache:apache /var/www/html/bludit
find /var/www/html/bludit -type d -exec chmod 755 {} \;
find /var/www/html/bludit -type f -exec chmod 644 {} \;

# IF SE Linux is enabled
getenforce
sestatus

setenforce 0

dnf install -y policycoreutils-python-utils
semanage fcontext -a -t httpd_sys_rw_content_t "/var/www/html/bludit/bl-content(/.*)?"
restorecon -Rv /var/www/html/bludit/bl-content
```
{% endcode %}

## Configure bludit.conf

```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html/bludit

    <Directory /var/www/html/bludit>
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog /var/log/httpd/bludit_error.log
    CustomLog /var/log/httpd/bludit_access.log combined
</VirtualHost>
```

## Final Commands

```bash
httpd -t
systemctl restart httpd
systemctl restart php-fpm 2>/dev/null || true
```

## Script

```bash
curl -fsSL https://pastebin.com/raw/deuzyJf6 | tr -d '\r' | sudo bash

# AI Citation - I used Claude to provide instruction steps for installing Bludit. 
# After completing the process by hand and seeing what worked and what didn't,
# I had Claude craft a script, which I checked for errors (it did have one!)
# After that, I tested it in on a base rocky image, which worked successfully.
```
