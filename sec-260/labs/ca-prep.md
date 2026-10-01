# CA Prep

On Host 2 (Certificate Authority):

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
openssl genrsa -out /root/cakey.pem 4096
```
{% endcode %}

On Host 1 (Web Server):

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
openssl genrsa -out /root/websrv.key 2048
```
{% endcode %}

On Host 2 (CA):

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
mkdir -p /etc/pki/CA/{certs,crl,newcerts,private}
cp /root/cakey.pem /etc/pki/CA/private/cakey.pem
chmod 600 /etc/pki/CA/private/cakey.pem
touch /etc/pki/CA/index.txt
echo 1000 > /etc/pki/CA/serial

openssl req -new -x509 -days 3650 -key /etc/pki/CA/private/cakey.pem -out /etc/pki/CA/cacert.pem
```
{% endcode %}

### Step 3: Generate the Certificate Signing Request (Host 1 — Web Server)

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
openssl req -new -key /root/websrv.key -out /root/websrv.csr
```
{% endcode %}

***

### Step 4: Securely Transfer the CSR to the CA

On Host 1 (Web Server):

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
scp /root/websrv.csr root@<CA-IP-address>:/root/
```
{% endcode %}

On Host 2 (Certificate Authority):

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
openssl ca -in /root/websrv.csr -out /root/websrv.crt -days 365
scp /root/websrv.crt root@<WebServer-IP-address>:/root/
```
{% endcode %}

On Host 2 (CA):

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
cat /etc/pki/CA/cacert.pem
```
{% endcode %}

On Host 1 (Web Server):

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
cat /root/websrv.key
cat /root/websrv.crt
```
{% endcode %}

```bash
dnf install mod_ssl -y

cp /root/websrv.crt /etc/pki/tls/certs/
cp /root/websrv.key /etc/pki/tls/private/

chmod 600 /etc/pki/tls/private/websrv.key # lock down the key

# copy the root CA so we can trust it

scp root@<CA-IP-address>:/etc/pki/CA/cacert.pem /root/
cp /root/cacert.pem /etc/pki/ca-trust/source/anchors/
update-ca-trust

nano /etc/httpd/conf.d/ssl.conf
```

Find and edit these two directives:

```apache
SSLCertificateFile /etc/pki/tls/certs/websrv.crt
SSLCertificateKeyFile /etc/pki/tls/private/websrv.key
```

```bash
firewall-cmd --permanent --add-service=https # open the firewall for https
firewall-cmd --reload

apachectl configtest
systemctl restart httpd
```

### Step 8: Verify

**Locally, from the Web Server:**

```bash
curl -vk https://localhost
```

**Decode:** `-v` verbose (shows the TLS handshake details), `-k` skip cert validation (useful here since the CA isn't in the _client's_ trust store yet, and CN won't match `localhost` anyway).

**From another machine, once the CA cert is distributed:**

```bash
curl -v --cacert cacert.pem https://<WebServer-IP-or-FQDN>
```

Check the log if anything fails:

```bash
tail -f /var/log/httpd/ssl_error_log
```

***

#### Quick Troubleshooting Reference

| Symptom                              | Likely Cause                                                       |
| ------------------------------------ | ------------------------------------------------------------------ |
| Apache won't start after restart     | Syntax error in `ssl.conf` — run `configtest` first                |
| "Permission denied" reading key/cert | SELinux context — run `restorecon`, or check `chmod`               |
| Browser: "certificate not trusted"   | Expected — client doesn't have `cacert.pem` in its trust store yet |
| Browser: "name mismatch"             | CN in the cert ("Joyce310") doesn't match the URL you're visiting  |
| Port 443 unreachable                 | Firewall rule missing — re-check `firewall-cmd --list-services`    |

Once you confirm `curl -vk https://localhost` returns a clean handshake and serves the default page, HTTPS is live. Let me know how the test goes and we can move on to a redirect from HTTP → HTTPS if you want that next.<br>
