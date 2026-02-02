# Apache CA Install

## Steps Required

* **Key generation**
  * Create Private Key
    * <pre class="language-bash"><code class="lang-bash"><strong>sudo mkdir /etc/ssl/mycerts
      </strong>sudo 
      </code></pre>
  * Generate/fetch .pem file under ssl/mycerts
    * ```bash
      cat /etc/ssl/mycerts/privatekey.priv
      openssl req -x509 -new -nodes -key /etc/ssl/mycerts/privatekey.priv -sha256 -days 365 -out /etc/ssl/mycerts/localhostCertificate.pem
      ```
* **Adding the Certificate to the server**
  * Create _**extra**_ folder under /usr/local/share/ca-certificates
    * ```
      mkdir /usr/local/share/ca-certificates/extra
      ```
  * Copy .pem file to /usr/local/share/ca-certificates/extra as .crt
    * ```
      cp localhostCertificate.pem /usr/local/share/ca-certificates/extra/localhostCertificate.crt
      ```
  * Update CA Certificates
    * `sudo update-ca-certificates`
  * Enable SSL
    * `sudo a2enmod ssl`
  *   Update the security configuration file

      * nano /etc/apache2/sites-available/default-ssl.conf
      * ![](../../.gitbook/assets/unknown.png)



      * SSLCertificateFile `PATH/TO/localhostCertificate.pem` &#x20;
      * SSLCertificateKeyFile `PATH/TO/privatekey.priv`
      * Restart Apache
        * systemctl restart apache2



Process:

```sql
Apache Server
   |
   |--(1) Generate private key: openssl genrasa -out /etc/ssl/mycerts/privatekey.priv 2048
   |--(2) Generate CSR (Certificate Signing Request): openssl req -new -key privatekey.priv -out ncaeserver.csr
   |
CA Server
   |
   |--(3) Review CSR
   |--(4) Sign CSR
   |--(5) Issue certificate
   |
Apache Server
   |
   |--(6) Install cert + key: mkdir /usr/local/share/ca-certificates/extra
   |-- cp certificate.pem /usr/local/share/ca-certificates/extra/ncaeChamplainApache.crt
   |-- sudo update-ca-certificates
   |--(7) Configure Apache SSL:
   |-- sudo a2enmod ssl
   |-- nano /etc/apache2/sites-available/default-ssl.conf
   
   SSLCertificateFile etc/ssl/mycerts/localhostCertificate.pem  
   SSLCertificateKeyFile PATH/TO/privatekey.priv

```



Extracting public key from private key:

```bash
openssl rsa -in mykey.pem -pubout > mykey.pub
```

Creating a certificate signing request:

```
# Generate a private key
openssl genrsa -out server.key 2048

# Generate a CSR
openssl req -new -key server.key -out server.csr
```

Example code block:

```
<VirtualHost *:443>
    ServerName champlain.ncae.com
    
    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/server.crt
    SSLCertificateKeyFile /etc/ssl/private/server.key
    SSLCertificateChainFile /etc/ssl/certs/ca-chain.crt  # If provided
    
</VirtualHost>
```

