# Week 12: Web Security

Lecture Slides: [Presentation](https://docs.google.com/presentation/d/1VowDm1_j5caX0phhVrgpjB-HxLR9eTNPnjNGzDFBkFU/edit?slide=id.g3a28d01ff4f_1_165#slide=id.g3a28d01ff4f_1_165)

### Vocabulary & Key Terms

#### Web Security

* Protecting websites, applications, and services from cyber threats.

#### SQL injection

* A way to input SQL code into form headers and fields to exploit a lack of sanitization

```sql
SELECT * FROM students WHERE studentId = 117 OR 1=1;
```

#### Command Injection

* Input that allows an attacker to execute commands on an operating system arbitrarily

#### Cross-Site Scripting

* A vulnerability allowing an attacker to insert malicious **client** scripts into a web page that is replicated to another individual
  * Stored: Scripts are saved
  * Reflected: Scripts result in a response
  * DOM-based: Vulnerability in the  client-side JavaScript

#### Cross-Site Request Forgery (CSRF)

* An attack that tricks authenticated users into executing actions that they do not want to do when they are logged in.

#### HTTP vs. HTTPS

* HTTP is transmitted over plain text, which is insecure
* HTTPS uses SSL/TLS, which encrypts data and ensures confidentiality and integrity.

#### CA Certificates

* Allow individuals to verify a website and communicate with it securely

#### Web Application Firewall (WAF)

* A firewall that operates on Layer 7, monitoring HTTP requests. Examples include ModSecurity, Cloudflare, and AWS WAF

#### Penetration Testing

* Simulated cyber attacks on computer systems to find vulnerabilities

#### Bug Bounty Programs

* Organizations offering money to find vulnerabilities

#### Static/Dynamic Security Testing

* Testing that tests the application source code without running it.&#x20;

### Main Ideas and Takeaways

#### Types of Vulnerabilities

* Weak Authentication: Weak passwords, missing MFA, no session timeout
* Broken Access Control: Users allowed to access stuff they shouldn't
* Security Misconfiguration: Default credentials unchanged, unnecessary features enabled
* Insufficient Logging/Monitoring

#### We secure websites through:

* Request Filtering: Based on predefined rules
* Allowlists and denylists: Have a rule set for preferably allowed URLs or have a deny list.
* Input Validation/Sanitization: Filter out bad SQL requests, cross-site scripting, and command injection attacks
* CSRF Tokens: Prevents a client from performing unauthorized actions
* HTTP Security Headers: These headers allow us to tell a browser how to handle content securely

#### Best Password Practices

* Use random, non-guessable
* At least 12 to 15 characters
* Use special characters, numbers, and capitalization

### Diagrams and Visuals

![](<../../.gitbook/assets/unknown (62).png>)

![](<../../.gitbook/assets/unknown (63).png>)

![](<../../.gitbook/assets/unknown (64).png>)

![](<../../.gitbook/assets/unknown (65).png>)

![](<../../.gitbook/assets/unknown (66).png>)

### Commands, Tools, or Techniques

{% embed url="https://owasp.org/Top10/" %}

* Burp Suite - Proxy that intercepts, inspects, and modifies traffic
* Nmap - Port mapping and discovery
* Wireshark - Packet inspection
* Browser Developer Tools - Inspect requests, cookies, and storage

\
\
<br>
