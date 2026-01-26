# Module 8: Hashing and Modern Ciphers

Lecture Slides: [Presentation](https://docs.google.com/presentation/d/1iq4DuIDijIqAeQjh442gWxf8IAg_s3Ko1Kktqag668o/edit?slide=id.ge546415ea0_2_230#slide=id.ge546415ea0_2_230)

### Vocabulary & Key Terms

#### Hash Function

* Used to check the integrity of files and non-repudiation. The message is arbitrary, and the hash is of fixed length. (Message Digest). It is impractical to revert, and it is resistant to attack.&#x20;
  * Digital Signatures are hashes!

#### Hash Collision

* When two hash digests with two different messages result in the same digest.&#x20;

#### Pseudorandmness

* Not truly random, but almost random, so it's impossible to tell otherwise. As random as it possibly can.

#### Hash Algorithms

* MD4
  * 128-bit digests, TLS certificates
* MD5
  * Security compromised, breakable
* SHA1
  * Designed by NSA
* SHA2
  * Designed by NSA

#### FIPS (Federal Information Processing Standard)

* Government regulations for how information needs to be processed.&#x20;

#### Rainbow Table

* List of common password hashes used to break passwords.

#### Salting

* Adding a random phrase before or after passwords before hashing it to make the hash harder to track.&#x20;

#### Steganography

* Hiding data in imagery.

#### Digital Certificates

* Certificates are provided by a Certificate Authority to verify the authenticity of a website. Comes with a public key to encrypt and send data to a website securely.
  * Typically uses RSA

### Main Ideas and Takeaways

* Hashes are used by anti-viruses to check for known viruses. Hashes can be used to sign messages because they can be repeated.&#x20;
* The longer the hash length, the stronger the hash

### Diagrams and Visuals

SHA 2 algorithms

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>



### Commands, Tools, or Techniques

* [John The Ripper](https://www.openwall.com/john/)
  * john --wordlist=rockyou.txt pass1.txt
* [Hashcat](https://hashcat.net/hashcat/)
  * hashcat -a 0 pass1.txt
* openssl
  * openssl passwd -1 1dollar
* Hashing
  * sha1sum file.txt
  * sha1sum file.txt > checksum.txt
  * sha1sum -c file.sha1
  * sha1sum -c checksum.txt
  * [http://www.fileformat.info/tool/hash.htm](http://www.fileformat.info/tool/hash.htm)
* [OpenStego](https://www.openstego.com/)
* [StegExpose](https://github.com/b3dk7/StegExpose)
* [StegDetect](https://github.com/abeluck/stegdetect)
* [Binwalk](https://github.com/ReFirmLabs/binwalk)

### Reflection & Questions

\
\
<br>
