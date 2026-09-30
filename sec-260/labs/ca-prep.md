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

<br>
