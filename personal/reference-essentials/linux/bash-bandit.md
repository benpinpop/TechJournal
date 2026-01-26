# Bash Bandit

## Level 0 Bandit0

Ls

Cat readme

### Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## Level 1 Bandit1

Pwd

Cat bandit1/\* or cat ./-

### Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## Level 2 Bandit2

ls

cat -- '--spaces in this filename--'

### Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## Level 3 Bandit3

Ls

Cd inhere

Ls -a (hidden file)

cat -- "...Hiding-From-You"

### Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## Level 4

Ls

Cd inhere

Cat – “file07”

### Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## Level 5

Ls -R -a - l | grep 1033

find . -type f -size 1033c -print

### Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## Level 6

find . -type f -user bandit7 -group bandit6 -size 33c

Redirect errors: 2>/dev/null

Final Command: find . -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null

./var/lib/dpkg/info/bandit7.password

Cat ./var/lib/dpkg/info/bandit7.password

### Password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## Level 7

cat data.txt | grep "millionth"

### Password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## Level 8

sort data.txt | uniq -u

sort — ensures duplicate lines are adjacent (required for uniq to work correctly)

uniq -u — prints only lines that appear exactly once<br>

To see counts, use uniq -c

### Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## Level 9

Use the strings command on the data.txt file to read it

strings data.txt –bytes=10

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
