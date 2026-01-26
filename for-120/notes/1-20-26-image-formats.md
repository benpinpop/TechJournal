# 1/20/26: Image Formats

### Overview

* Raw Images (dd)
* EnCase EWF (E01)
* FTK SMART
* Advanced Forensic Format (AFF)

### DD

* Bit-by-bit copy
* Copies all the empty data, which can be super big. Does not contain any metadata about the image file; it will be the same.&#x20;

#### What's missing?

* Cryptographic hashing
* Error handling
* Logging
* Performance enhancements like compression
* Verification checks, and progress monitoring

### EnCase EWF (E01)

* Expert Witness Format (EWF)
* Supportsmetadata, compression, encryption, hashing, and split files
* Called evidence containers

#### Metadata details

* Hashes
* Drive geometry (bytes/sectors)
* Timestamps
* Chain of Custody
* **Hashes will be different based upon metadata**

### FTK SMART

* Access Data

### AFF

* All expected features and additional encryption
* Open Source
