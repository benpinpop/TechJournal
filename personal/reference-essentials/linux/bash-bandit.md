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

## Level 8

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

strings data.txt –bytes=10
```
{% endcode %}



### Password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## Level 10

The file is in base64, to decode, use base -d data.txt

### Password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

## Level 11

cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

A-Z goes from N-Z and A-M, same for lowercase.

### Password: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

## Level 12

xxd - Provides a hexadecimal dump of a file. Use -r to reverse the hex dump. Use | head to read the top part of the file.&#x20;

The first few hex numbers indicate the zip type of the file. See [https://en.wikipedia.org/wiki/List\_of\_file\_signatures](https://en.wikipedia.org/wiki/List_of_file_signatures) to compare the first bytes and find the type of file compression the file is. Rename the file to ensure it decrypts properly.&#x20;

### Password: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
