# Bash Bandit

## Level 0 Bandit0

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
ls # Outputs our directory
cat readme # Outputs the readme file
```
{% endcode %}

{% hint style="success" %}
Password: 6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR
{% endhint %}

## Level 1 Bandit1

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
pwd # Prints the working directory
cat /home/bandit1/* # To print all files OR
cat ./- # Treats it as a file path instead of an option
```
{% endcode %}

{% hint style="success" %}
Password: PK8fYLZg2hnHSz83plBL1iEPKdD3QToB
{% endhint %}

## Level 2 Bandit2

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
ls
cat -- '--spaces in this filename--' # the -- tells us that there are no more options to read.
```
{% endcode %}

{% hint style="success" %}
Password: 7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
{% endhint %}

## Level 3 Bandit3

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
ls
cd inhere
ls -a (hidden file)
cat ...Hiding-From-You
```
{% endcode %}

{% hint style="success" %}
Password: xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq
{% endhint %}

## Level 4

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
ls
cd inhere
file ./*
cat -- -file07
```
{% endcode %}

{% hint style="success" %}
Password: 6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG
{% endhint %}

## Level 5

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
human-readable
1033 bytes in size
not executable

find . -type f -size 1033c -print
```
{% endcode %}

{% hint style="success" %}
Password: pXa26xhMWaC2SvDotA4r9EgZkulOeSBW
{% endhint %}

## Level 6

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
find . -type f -user bandit7 -group bandit6 -size 33c

Redirect errors: 2>/dev/null

Final Command: find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null

./var/lib/dpkg/info/bandit7.password

cat ./var/lib/dpkg/info/bandit7.password
```
{% endcode %}

{% hint style="success" %}
Password: Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3
{% endhint %}

## Level 7

<pre data-title="" data-overflow="wrap" data-line-numbers data-expandable="true"><code><strong>The password for the next level is stored in the file data.txt next to the word millionth
</strong>
cat data.txt | grep "millionth"
</code></pre>

{% hint style="success" %}
Password: VR1ljMayciFxbnUokuQmJFw6QC9VKtub
{% endhint %}

## Level 8 (Up to date)

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

sort data.txt | uniq -u
sort — ensures duplicate lines are adjacent (required for uniq to work correctly)
uniq -u — prints only lines that appear exactly once

To see counts, use uniq -c
```
{% endcode %}

{% hint style="success" %}
Password: EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl
{% endhint %}

## Level 9

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
Use the strings command on the data.txt file to read it
strings data.txt –bytes=12
```
{% endcode %}

{% hint style="success" %}
Password: B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
{% endhint %}

## Level 10

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
The file is in base64, to decode, use 

base64 -d data.txt
```
{% endcode %}

{% hint style="success" %}
Password: pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro
{% endhint %}

## Level 11

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

A-Z goes from N-Z and A-M, same for lowercase.
```
{% endcode %}

{% hint style="success" %}
Password: GROozWPO8QyN0mGrjUkID0WCYkZiQxrN
{% endhint %}

## Level 12

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
xxd - Provides a hexadecimal dump of a file. Use -r to reverse the hex dump. Use | head to read the top part of the file. 

The first few hex numbers indicate the zip type of the file. See https://en.wikipedia.org/wiki/List_of_file_signatures to compare the first bytes and find the type of file compression the file is. Rename the file to ensure it decrypts properly.

1f8b 0808 corresponds to gz (gzip)
425a 6839 corresponds to .bz (bzip2) files
6461 7461 362e 6269 6e00 is a TAR file

gzip -d
bzip2 - d
tar -xf file

Use XXD to read the head of the file, and then decode accordingly.
```
{% endcode %}

{% hint style="success" %}
Password: qQYQiHOBPR8zR61qxYqX45quvihF2uzk
{% endhint %}

## Level 13

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14

Copy sshkey.private to your machine, chmod 600 the permissions

ssh -p 2220 -i sshkey.private bandit14@bandit.labs.overthewire.org
```
{% endcode %}

{% hint style="success" %}
Password: aaWecNkG4FhxJQxz07uiwzVP6bJiYS65
{% endhint %}

## Level 14

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

nc 127.0.0.1 30000
Copy and paste the password.
```
{% endcode %}

{% hint style="success" %}
Password: pbLYuZtTg4MgaqfJx8jbA9gKKGqM68A7
{% endhint %}

## Level 15

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

openssl s_client -connect localhost:30001
```
{% endcode %}

{% hint style="success" %}
Password: kS0Hf0u5HiXFwKMKFqXvPdOTNGGa0X8V
{% endhint %}

## Level 16

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
nmap -p 31000-32000 127.0.0.1
nmap -p 31046,31518,31691,31790,31960 -sV 127.0.0.1

openssl s_client -connect localhost:31790 -quiet
```
{% endcode %}

{% hint style="success" %}
Password: Provided via SSH key.
{% endhint %}

## Level 17

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

diff passwords.new passwords.old
```
{% endcode %}

{% hint style="success" %}
Password: OQxXZjELndr90zuhOTDYBEomI0SZITXI
{% endhint %}

## Level 18

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

ssh -p 2220 bandit18@bandit.labs.overthewire.org ls
ssh -p 2220 bandit18@bandit.labs.overthewire.org cat readme
```
{% endcode %}

{% hint style="success" %}
Password: KpsOfPkcP7i1FlIExk2QEjyt6dw8dxZI
{% endhint %}

## Level 19

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

./bandit20-do cat /etc/bandit_pass/bandit20
```
{% endcode %}

{% hint style="success" %}
Password: 4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA
{% endhint %}

## Level 20

{% code title="" overflow="wrap" lineNumbers="true" expandable="true" %}
```
echo '4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA' | nc -lp 9999 &
./suconnect 9999
```
{% endcode %}

{% hint style="success" %}
Password: bW9kBv5WC3P4yoDyf12LSdGuNz5ka6hY
{% endhint %}
