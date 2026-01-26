# Capture The Flag

## Crypto

A mix of cryptography challenges.

### Crypto 101

Given a specific ciphertext, we have been told to provide the flag. The ciphertext is below:

{% code title="ciphertext.txt" %}
```
FB WDOHRCQDPHEO, P TAMTRFRARFCB WFHEID FT P NIRECG CY IBWDOHRFBQ MO VEFWE ABFRT CY HJPFBRIXR PDI DIHJPWIG VFRE WFHEIDRIXR, PWWCDGFBQ RC P YFXIG TOTRIN; REI "ABFRT" NPO MI TFBQJI JIRRIDT (REI NCTR WCNNCB), HPFDT CY JIRRIDT, RDFHJIRT CY JIRRIDT, NEXRADIT CY REI PMCLI, PBG TC YCDRE. REI DIWIFLID GIWFHEIDT REI RIXR MO HIDYCDNFBQ REI FBLIDTI TAMTRFRARFCB.

TAMTRFRARFCB WFHEIDT WPB MI WCNHPDIG VFRE RDPBTHCTFRFCB WFHEIDT. FB P RDPBTHCTFRFCB WFHEID, REI ABFRT CY REI HJPFBRIXR PDI DIPDDPBQIG FB P GFYYIDIBR PBG ATAPJJO UAFRI WCNHJIX CDGID, MAR REI ABERT REINTIJLIT PDI JIYR ABWEPBQIG. MO WCBRDPTR, FB P TAMTRFRARFCB WFHEID, REI ABFRT CY REI HJPFBRIXR PDI DIRPFBIG FB REI TPNI TIUAIBWI FB REI WFHEIDRIXR, MAR REI ABFRT REINTIJLIT PDI PJRIDIG.

REIDI PDI P BANMID CY GFYYIDIBR ROHIT CY TAMTRFRARFCB WFHEID. FY REI WFHEID CHIDPRIT CB TFBQJI JIRRIDT, FR FT RIDNIG P TENHJI TAMTRFRARFCB WFHEID; P WFHEID REPR CHIDPRIT CB JPDQID QDCAHT CY JIRRIDT FT RIDNIG HCJOQDPHEFW. P NCBCPJHEPMIRFW WFHEID ATIT YFXIG TAMTRFRARFCB CLID REI IBRFDI NITTPQI, VEIDIPT P HCJOPJHEPMIRFW WFHEID ATIT P BANMID CY TAMTRFRARFCBT PR GFYYIDIBR HCTFRFCBT FB REI NITTPQI, VEIDI P ABFR YDON REI HJPFBRIXR FT NPHHIG RC CBI CY TILIDPJ HCTTFMFJFRFIT FB REI WFHEIDRIXR PBG LFWI LIDTP. REI YJPQ FT BC TAMTRFRARI WPB TRCH NI, PJJ JCVIDWPTI, VFRECAR REI THPWIT.
```
{% endcode %}

The first step we need to follow here is to identify what type of cipher it is. A quick check confirms that it isn't a [Caesar](https://cryptii.com/pipes/caesar-cipher) or [Atbash](https://cryptii.com/pipes/atbash-cipher) Cipher.&#x20;

In Atbash Ciphers, we'll typically see many end characters in the alphabet. For example, when converting the message:

{% code title="plaintext.txt" fullWidth="false" %}
```
If he had anything confidential to say, he wrote it in cipher, that is, by so changing the order of the letters of the alphabet, that not a word could be made out.
```
{% endcode %}

We'll see something like this:

{% code title="ciphertext.txt" %}
```
Ru sv szw zmbgsrmt xlmurwvmgrzo gl hzb, sv dilgv rg rm xrksvi, gszg rh, yb hl xszmtrmt gsv liwvi lu gsv ovggvih lu gsv zokszyvg, gszg mlg z dliw xlfow yv nzwv lfg.
```
{% endcode %}

We can easily rule out the Caesar cipher by shuffling through all 25 combinations. We can use [identifier](https://www.boxentriq.com/code-breaking/cipher-identifier) [tools](https://www.dcode.fr/cipher-identifier) to narrow down our search. The websites give separate results, but allow us to zoom in on one type of cipher.

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption><p>boxentriq.com</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption><p>dcode.fr</p></figcaption></figure>

While one website suggests this is a two-square horizontal cipher, both websites suggest the ciphertext is a substitution cipher. Luckily, some [websites](https://www.guballa.de/substitution-solver) can brute force these ciphertexts, saving us from a painstaking manual decryption process. Inputting this ciphertext into the linked websites fetches us results!

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption><p>guballa.de/substitution-solver</p></figcaption></figure>

{% code title="plaintext.txt" %}
```
IN CRYPTOGRAPHY, A SUBSTITUTION CIPHER IS A METHOD OF ENCRYPTING BY WHICH UNITS OF PLAINTEXT ARE REPLACED WITH CIPHERTEXT, ACCORDING TO A FIXED SYSTEM; THE "UNITS" MAY BE SINGLE LETTERS (THE MOST COMMON), PAIRS OF LETTERS, TRIPLETS OF LETTERS, MHXTURES OF THE ABOVE, AND SO FORTH. THE RECEIVER DECIPHERS THE TEXT BY PERFORMING THE INVERSE SUBSTITUTION.

SUBSTITUTION CIPHERS CAN BE COMPARED WITH TRANSPOSITION CIPHERS. IN A TRANSPOSITION CIPHER, THE UNITS OF THE PLAINTEXT ARE REARRANGED IN A DIFFERENT AND USUALLY QUITE COMPLEX ORDER, BUT THE UNHTS THEMSELVES ARE LEFT UNCHANGED. BY CONTRAST, IN A SUBSTITUTION CIPHER, THE UNITS OF THE PLAINTEXT ARE RETAINED IN THE SAME SEQUENCE IN THE CIPHERTEXT, BUT THE UNITS THEMSELVES ARE ALTERED.

THERE ARE A NUMBER OF DIFFERENT TYPES OF SUBSTITUTION CIPHER. IF THE CIPHER OPERATES ON SINGLE LETTERS, IT IS TERMED A SHMPLE SUBSTITUTION CIPHER; A CIPHER THAT OPERATES ON LARGER GROUPS OF LETTERS IS TERMED POLYGRAPHIC. A MONOALPHABETIC CIPHER USES FIXED SUBSTITUTION OVER THE ENTIRE MESSAGE, WHEREAS A POLYALPHABETIC CIPHER USES A NUMBER OF SUBSTITUTIONS AT DIFFERENT POSITIONS IN THE MESSAGE, WHERE A UNIT FRYM THE PLAINTEXT IS MAPPED TO ONE OF SEVERAL POSSIBILITIES IN THE CIPHERTEXT AND VICE VERSA. THE FLAG IS NO SUBSTITUTE CAN STOP ME, ALL LOWERCASE, WITHOUT THE SPACES.

```
{% endcode %}

There seem to be several typos, which can be attributed to the process I used to extract the ciphertext from the virtual machine. Copy and pasting is non-functional, so the text was extracted from a screenshot. Finally, we are given the flag:

```
NO SUBSTITUTE CAN STOP ME
```

We are told to enter in lowercase, without spaces, and we get the answer!

### Crypto 201

## Reverse Engineering

### Reversing 101

### Reversing 102

## Trivia

### Trivia 101

**This trivia question asks how many possible IVs the WEP protocol can use.**&#x20;

WEP is a deprecated security algorithm for WiFi connections. Using a 10- or 26-digit hexadecimal key, WEP was considered widely secure; however, a bug was discovered in the algorithm in 2001. WEP is now deprecated, and more modern algorithms are in use, like WPA2. When creating the encryption key, WEP uses a **24-bit** initialization vector. Knowing this, we can calculate our answer, which would be 2<sup>24</sup>.&#x20;

The answer is: **16777216**

### Trivia 102

**The question asks about the PS3 master key.**&#x20;

The answer can be found by identifying the hexadecimal master key, which is posted [here](https://yalelawtech.org/2011/03/01/46-dc-ea-d3-17-fe-45-d8-09-23-eb-97-e4-95-64-10-d4-cd-b2-c2/).

The answer is: **46DCEAD317FE45D80923EB97E4956410D4CDB2C2**

### Trivia 103

The question asks about a W95 computer infected with a backdoor that is listening on UDP port 31337. The question states that the malware's packets use the same first 8 bytes, and we are asked to identify them.

Our first step here is to identify which piece of malware uses the UDP port 31337. Some websites identify services that use specific ports, so we can Google these. The first [two](https://www.speedguide.net/port.php?port=31337) [results](https://www.cbtnuggets.com/common-ports/what-is-port-31337) are extremely useful, and tell us that the service is used by an infamous backdoor called **Back Orifice**.&#x20;

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption><p>speedguide.net</p></figcaption></figure>

Knowing our malware, we need to find either a packet file of the malware or a paper that describes the packet. A bit of googling leads us to a [GIAC paper on the Trojan](https://www.giac.org/paper/gcih/306/tracking-orifice-trojan-university-network/101743). A little scrolling, and Ctrl + F for "8 bytes" leads us to a paragraph that describes the packets that Back Orifice sends.

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption><p>giac.org</p></figcaption></figure>

Our answer is: **\*!\*QWTY?**
