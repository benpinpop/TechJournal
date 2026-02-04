# Apache Hardening

```bash
sudo apt install libapache2-mod-security2
sudo mv /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf
sudo nano /etc/modsecurity/modsecurity.conf

SecRuleEngine On

sudo apt install modsecurity-crs
sudo a2enmod security2

sudo systemctl restart apache2

/var/log/apache2/modsec_audit.log

```
