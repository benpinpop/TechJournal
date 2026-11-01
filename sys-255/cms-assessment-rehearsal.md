# CMS Assessment Rehearsal

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
dnf install httpd php php-cli php-json php-mbstring php-xml php-gd wget -y

systemctl start httpd
systemctl enable httpd

sudo chown -R apache:apache /var/www/html/
sudo chmod -R 755 /var/www/html/

# Installing HTMLy
cd /
wget https://github.com/danpros/htmly/archive/refs/tags/v3.1.1.zip
```
{% endcode %}
