# Module 7: Cryptography Basics

Lecture Slides: [Presentation](https://docs.google.com/presentation/d/1YITdV_2j2sLdoUkUhhCiexDNic4MF9XXOgMLwIJ0VXw/edit?slide=id.ge546415ea0_2_84#slide=id.ge546415ea0_2_84)

### Vocabulary & Key Terms

#### Cryptography

* The art of writing and solving codes

#### Cryptology

* The study of cryptography

#### Cipher

* Method or way to disguise and hide text

#### Plaintext

* The original form of the text, i.e a decrypted form of text.

#### Encrypt

* The process of hiding information using a cipher.

#### Decrypt

* The process of revealing the information using the same cipher. Encrypting with one cipher and decrypting with another will not work 99% of the time.

#### Non-Repudiation

* Creating proof that a user did something beyond a reasonable doubt.
  * Signing messages

#### Multi-Factor Authentication (MFA)

* Ensuring that someone is who they claim to be through at least 2 factors
  * What you know (Knowledge)
    * Username, Password, Security Questions
  * What you have (Possession)
    * Key card, email address, or USB pass card.
  * What you are (Biological)
    * Facial recognition or fingerprint.
* BKP, Biological, Knowledge, or Possession

#### Symmetric vs. Asymmetric Encryption

* Symmetric encryption uses one key, whereas asymmetric encryption uses two keys, one for encrypting and one for decrypting.&#x20;
  * Symmetric: Typically faster than asymmetric, requires one key
    * Examples include the Atbash (Reverse Alphabet) or Caesar Cipher (Shift).
    * Data in Transit: SSL, TLS, SSH
    * Data at Rest: AES (Advanced Encryption Standard)
  * Asymmetric: Uses two mathematically linked keys using prime numbers in the 2<sup>2048</sup> range. A public key is made available to everyone who encrypts text, and a private key is used to decrypt.
    * Helpful for sending data to people without it being intercepted.
    * Even if you have the public key, you can't decrypt.
    * The most common known example is RSA (Rivest-Shamir-Adleman)
    * In asymmetric encryption, all you need is to give out the public key, and you don't need to exchange keys.

#### Digital Certificates

* Digital certificates a way to verify the authenticity of a user, website, or file. The digital certificate contains a public key for the connection and is signed by a certificate authority (CA).&#x20;

#### Hashing

* Hashing is like encryption, but it instead only goes one way. After you've created a hash, there is no computationally effective way to go back. Hashes are a way of checking data integrity.
  * Used for signatures

### Main Ideas and Takeaways

* Encryption and Hashing are used everywhere on the internet, from browsing to downloading and opening files. Without encryption, we would have no privacy at all.
* Encryption is extremely effective, but quantum computers pose a risk to modern encryption algorithms.

### Diagrams and Visuals

![](<../../.gitbook/assets/unknown (2).jpeg>)

![](<../../.gitbook/assets/unknown (1) (1) (1) (1).png>)

![](<../../.gitbook/assets/unknown (2) (1) (1).png>)

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

![](<../../.gitbook/assets/unknown (4) (1) (1).png>)

### Commands, Tools, or Techniques

* GPG (Asymmetric)
  * gpg --full-generate-key
    * Create a key
  * gpg –list-keys
    * List current keys
  * gpg --encrypt --recipient "NAME" secret.txt
    * Output is a .gpg file
  * gpg --output decrypted.txt --decrypt secret.txt.gpg
* Mcrypt (Symmetric)
  * mcrypt --list
    * List all supported methods
  * mcrypt message.txt
    * Encrypts file
  * mcrypt -d message.txt.nc
    * Decrypts file

{% embed url="https://cryptii.com/pipes/caesar-cipher" %}

{% embed url="https://www.boxentriq.com/code-breaking/atbash-cipher" %}

### Reflection & Questions

\
\
<br>
