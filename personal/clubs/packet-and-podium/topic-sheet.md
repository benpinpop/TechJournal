# Topic Sheet

### Old Topic List

* Computer forensics
* Mobile device forensics
* Network forensics
* Data forensics & analysis
* IoT Forensics
* How to tell deepfakes from non deepfakes
* Memory forensics, how to extract a memory image
* Vehicle forensics
* AI DF detection
* Malware detection and tracking
  * Analyzing artifacts
* Ethics
  * Hacking back
* Cyber warfare simulations
* Social Engineering and specific factors, how to properly socially engineer something
* How do compression algorithms work?
* Detecting insider threats
  * What are the human factors?
* Encrypted traffic analysis
* Zero-day exploit tracing
* Anti-forensics techniques / Anti-sandboxing and how to do it
* DNS tunneling
  * Detection and how it's done
* Using DNS filters to block ads
* Password cracking
  * Evolution
  * Tactics
* Analyzing browser activity
* How cyber threat intelligence is shared (CISA, etc)
* Non-repudiation: how do hashes prove non-repudiation, and **how can they be modified**?
* Encryption and Hashing
  * How does encryption or hashing work?
  * Is there any way to break encryption and/or hashing?
  * What does a single round of encryption look like
  * Modulo, XOR
  * Quantum cryptography threats
* Device fingerprinting, Browser fingerprinting
* How do cookies track you?
* Cold boot attacks
* Space-based attacks: how do you communicate with satellites?
* Management and Server Software
  * Kubernetes
  * Microsoft Azure
  * APIs & REST APIs
* Deanonymizing Tor users through side channels
* How to track crypto transactions
* Ransomware negotiation tactics
* VM configuration

### Forensics & artifact analysis

1. Cross-platform timeline reconstruction (Windows, macOS, Linux, Android, iOS).
2. File system forensics: NTFS, APFS, ext4 differences and recovery strategies.
3. Live vs. dead forensics: tradeoffs for volatile artifact collection.
4. Browser forensics: PWAs, IndexedDB, service workers, and artifact persistence.
5. Cloud-storage artifact analysis (OneDrive, Google Drive, Dropbox).
6. Container forensics: Docker images, container escape artifacts, and provenance.
7. Memory carving: locating in-memory files and decrypted blobs.
8. USB/device attach/remove artifact analysis across platforms.
9. Email forensics: headers, DKIM/SPF/DMARC traces, and forging detection.
10. Forensic analysis of encrypted containers (e.g., VeraCrypt) at a metadata level.

### Network, traffic, and detection

11. Encrypted traffic analysis using metadata and flow features (no decryption).
12. DNS abuse detection: fast-flux, DGA, and domain reputation pipelines.
13. TLS/SSL fingerprinting for client and malware identification.
14. Covert channels over allowed protocols (identification and mitigation).
15. Network packet-by-packet versus flow-based detection: strengths and use-cases.
16. BGP hijacks and attribution: when routing changes signal compromise.
17. IoT network profiling for anomaly detection.
18. Active network scanning artifacts: how defenders detect reconnaissance.
19. Passive monitoring for insider data exfiltration (SFTP, cloud uploads, steganography).
20. Industrial Control Systems (ICS) network forensics and anomaly indicators.

### Malware, reverse engineering & tracking

21. Behavioral profiling of malware families using sandbox telemetry.
22. Correlating C2 infrastructure across campaigns (infrastructure similarity graphs).
23. Ransomware lineage analysis and negotiation decision frameworks (ethical/legal focus).
24. Malware persistence mechanisms across OSes and detection heuristics.
25. Memory-only malware: detection challenges and heuristic signals.
26. Supply-chain malware detection and provenance verification.
27. Malware packing/obfuscation evolution and unpacking strategies (defensive).
28. Attribution pitfalls: false flags, reused infrastructure, and robust reporting practices.
29. Staged payload analysis: how to triage multi-stage attacks.
30. Emulation vs. hardware-based analysis: evasion techniques and countermeasures.

### Cryptography, hashing & crypto-analysis

31. Practical differences: symmetric vs. asymmetric vs. hashing (simple, clear examples).
32. Hash collision case studies and practical implications for integrity.
33. Side-channel signals that leak cryptographic keys (timing, power) — high-level survey.
34. Post-quantum cryptography: candidate algorithms, deployment challenges.
35. Cryptographic misuse in real world (bad IVs, key reuse, weak RNGs).
36. Encrypted traffic metadata used for de-anonymization and detection.
37. Crypto wallet forensics and seed phrase leakage vectors (defensive).
38. Secure multi-party computation and forensics implications.
39. Provable non-repudiation: legal vs. technical guarantees and limits.
40. Practical demonstration: what a single round of a block cipher does (visual/interactive).

### AI, deepfakes & detection

41. Deepfake detection arms race: features that survive model updates.
42. Detecting synthetic audio: spectral and linguistic artifacts.
43. AI-generated text detection: pitfalls and evasion.
44. Using explainable AI for DFIR triage (why an alert was raised).
45. Synthetic media provenance tracking (watermarking and metadata schemes).
46. Generative model poisoning and integrity risks.
47. AI-assisted malware: automated polymorphism & defensive detection approaches.
48. Red-team/blue-team AI simulations for incident response.
49. Bias and fairness in threat-detection ML pipelines.
50. Evaluating robustness of DFIR tools against adversarial examples.

### Privacy, anonymity & deanonymization

51. Tor deanonymization side-channels: high-level review and ethical mitigation.
52. Device and browser fingerprinting: cross-site tracking defenses.
53. Cookie and storage partitioning: browser privacy design and limitations.
54. Deanonymizing crypto transactions via cluster analysis and off-chain links (defensive/forensic).
55. Cross-correlation of OSINT sources to build link graphs (ethical use cases).
56. Privacy-preserving telemetry for security monitoring.
57. Differential privacy: how it applies to threat intelligence sharing.
58. Mobile app privacy leaks: covert channels and mitigations.
59. Measuring effectiveness of browser privacy features (tests & metrics).
60. Ethics of de-anonymization research and responsible disclosure.

### Human factors, social engineering & insider threats

61. Social-engineering case studies: successful campaigns and why they worked.
62. Psychological triggers: reciprocity, urgency, authority — defensive training modules.
63. Phishing simulation program design and measurement of behavior change.
64. Measuring insider threat risk: behavioral baselines and privacy considerations.
65. Linguistic analysis for spear-phishing detection (writing-style models).
66. Gamified red-team training for social engineering awareness.
67. Cultural factors in cyber deception and response.
68. Human-in-the-loop detection systems: benefits and failure modes.
69. Ethics and legality of honeypots aimed at human attackers.
70. Trade-offs of aggressive user monitoring for insider detection (privacy vs. security).

### Cloud, DevOps, and management

71. Kubernetes forensics: pod lifecycle artifacts, audit logs, and misconfiguration traps.
72. Cloud-native incident response runbooks for Azure/AWS/GCP differences.
73. Infrastructure-as-Code drift detection and security implications.
74. API abuse detection: credential stuffing, API key leakage, throttling anomalies.
75. Secrets management mistakes and forensic artifacts.
76. Server-side request forgery (SSRF) impact on cloud metadata exposure (defensive study).
77. CI/CD pipeline compromise scenarios and containment strategies.
78. Multi-cloud logging consolidation for forensic readiness.
79. Hardening container registries and detecting tampered images.
80. TPM and secure boot for server integrity verification.

### Emerging tech & unusual domains

81. Vehicle forensics: CAN bus analysis, telematics logs, and EV-specific artifacts.
82. Space/ground-satellite communications security and forensic logging challenges.
83. Smart city attack surfaces: street sensors, traffic signals, public Wi-Fi.
84. Wearables forensics: health data artifacts and privacy concerns.
85. IoT firmware analysis and proving supply-chain compromise.
86. Cold-boot attacks and hardware reliability of RAM remanence.
87. 5G slicing and forensic challenges in virtualized RANs.
88. Quantum key distribution: practical limitations and forensic traces.
89. Home router compromise: persistence and lateral movement patterns.
90. Smart building forensics: HVAC, access control logs, and sensor tampering signs.

### Anti-forensics, evasion & ethics

91. Anti-forensics techniques survey: what works—and what doesn't—for modern defenders.
92. Anti-sandbox techniques used by modern malware and defensive mitigations.
93. Detection vs. deception: ethical considerations of offensive countermeasures (e.g., “hacking back”).
94. Legal frameworks and policy proposals for active cyber defense.
95. Designing forensics-resistant systems: is it possible without harming users?
96. Forensic artifact falsification detection: signs of tampering.
97. Responsible disclosure processes when research reveals exploitable anti-forensic methods.
98. Building audit trails that are tamper-evident (blockchain/hardware-backed approaches).
99. Ethical simulation of insider attacks for testing detection systems.
100. Comparative law: cybercrime statutes and cross-border evidence collection.
