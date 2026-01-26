# Module 6: System Security

Lecture Slides: [Presentation](https://docs.google.com/presentation/d/1QCHrWqEUO80mKF2cbASZHvpKWNcnarGsdjhw483_P0g/edit?usp=sharing)

### Vocabulary & Key Terms

Define important terms and acronyms related to the topic of the module.

#### System Security

* Measures and practices put in place to protect computer systems, networks, and data from unauthorized access, damage, or theft

#### Malware

* Malicious software designed to harm, spy on, or take control of systems

#### Man-in-the-middle

* When a hacker secretly intercepts communication between parties, typically over a network

#### Insider Threat

* A threat from inside an organization

#### Social Engineering

* Tricking people into giving info away

#### Denial of Service

* Flooding a system with traffic so that no one else can access that system

#### Access Control

* Controlling who can access systems and what they can do with those systems.
  * Discretionary -  Owner decides who can access
  * Mandatory - Based on security labels
  * Role-Based - Access based on the role
  * Attribute-Based: Based on attributes like location, role or time of access.

#### Least Privelege

* The idea that you should give the least access possible to users, only what they **need.**
  * Time-Based access, restricting use to working hours
  * Geo-fencing, only allowing users to work inside the building

#### IoT (Internet of Things)

* Devices that are interconnected using the internet
  * Badge readers, motion detectors, smart thermostats.

### Main Ideas and Takeaways

Bullet points for notes that aren’t definitions, but explain how things work or why things are important. Feel free to bold/highlight the most important information.

* Monitor your systems, physically and digitally, for threats.&#x20;
  * Access Control: Keycards, PINs, Biometrics
  * Surveillance: CCTV, Security Guards, Alarms
  * Perimeter: Fences, locks, doors
  * Monitoring tools: SIEM, SOAR, XDR

System Security is not just digital; physical security is extremely important.

### Diagrams and Visuals

Include images from the slides or from the internet that are useful and/or good references.

![](<../../.gitbook/assets/unknown (41).png>)

![](<../../.gitbook/assets/unknown (42).png>)

![](<../../.gitbook/assets/unknown (43).png>)

![](<../../.gitbook/assets/unknown (44).png>)

![](<../../.gitbook/assets/unknown (36).png>)

![](<../../.gitbook/assets/unknown (37).png>)

![](<../../.gitbook/assets/unknown (38).png>)

![](<../../.gitbook/assets/unknown (39).png>)

![](<../../.gitbook/assets/unknown (40).png>)

### Commands, Tools, or Techniques

* Commands
  * chmod - Modifies a file.
    *   Read (r): Value 4

        Write (w): Value 2

        Execute (x): Value 1<br>

        0: No permissions (---)

        1: Execute only (--x)

        2: Write only (-w-)

        3: Write and execute (-wx) (2 + 1)

        4: Read only (r--)

        5: Read and execute (r-x) (4 + 1)

        6: Read and write (rw-) (4 + 2)

        7: Read, write, and execute (rwx) (4 + 2 + 1)
    * chmod 600 file2
      * 6 - Owner can read and write
      * 0 - Group has no permissions
      * 0 - Others have no permissions
  * chown - Checks who owns a file, includes owner and group.
  * passwd - Changes the password
  * whoami - Lists teh current user
  * useradd - Creates a new user account
  * usermod - Modifies a user
    * sudo usermod -aG group1 username
      * Adds group1 to username
  * id - List user ID and groups with IDs
  * groups - Lists user groups
  * su - Change users (with password)
  * sudo - Run commands as admin. Necessary for any commands&#x20;
  * ls -l - List file permissions
* File Locations
  * /etc/shadow
* Time Based Login
  * Location: /etc/security/time.conf
  * username;\*;tty1;Al0800-1700
* Restrict SSH logins
  * Location: /etc/hosts.allow and /etc/hosts.deny

### Reflection & Questions

\
\
<br>
