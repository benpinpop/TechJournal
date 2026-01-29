# Operation Shadow Breach

## Questions

1. Describe the complete attack path you took from initial recon to gaining SSH access. What were the critical steps?
   1. We identified server versions, email addresses, and scanned for a port for remote access. After remote access was identified, we tried to locate a password for an attack. The critical steps were really just identifying user credentials and remote access permissions.&#x20;
2. If you were TechNova's security team, at which stage do you think you could have detected this attack? How?
   1. I think they could have detected this attack during the port scan. If they identified a port scan, they could have blocked our IP. Additionally, failed SSH login requests could also be a key indicator of attempted compromise. Cross-referencing IP traffic from the website + port scan + SSH logins could also be key in identifying threat actors, though this is difficult across multiple log files.
3. Rate the severity of the Apache 2.4.49 vulnerability on a scale of 1-10. Justify your rating using CVSS scores and business context.
   1. Honestly, this seems more like an 8, as it does require a little effort to detect. CVSS 3.0 says it's a 7.5. The ability for RCE is pretty dangerous as well, so it's definitely high up there.&#x20;
4. After reading the risk acceptance form, explain WHY TechNova chose to keep the vulnerable server running instead of patching immediately.
   1. They had services that were compatible with the current versions, and updating would require at a minimum $50k. They were waiting for a contract renewal to update systems, so they thought the risk was acceptable. It probably wasn't,
5. Do you agree or disagree with TechNova's decision? Support your answer with specific reasoning about business vs. security trade-offs.
   1. I understand that 2.4 million is at risk if they upgrade, but there may be more in lawsuit damages as a result of a server getting hacked. I think as a Cybersecurity (aspiring) professional, any risk is unacceptable here for larger companies, but that is a lot of revenue. The security risks, on the other hand, may be losing access to the server entirely, ransomware, etc, etc.&#x20;
6. What compensating controls (safety measures) did TechNova put in place to reduce risk while keeping the vulnerable server running?&#x20;
   1. They isolated it in its own internal subnet, making it only accessible to the internal network. This significantly reduces the attack surface.
7. Are these compensating controls adequate? What additional controls would you recommend?
   1. I'd say they're somewhat adequate, although if a vendor or client system is compromised, they may be able to access the isolated box. I would just recommend changing the configuration to at least patch the critical vulnerability, as indicated by the NVD database.
8. Is it ethical for a company to knowingly run vulnerable systems?
   1. Yes, as long as the risk is properly mitigated. In this circumstance, we had internal network access, so we could access their system. Companies run vulnerable systems all the time, for example, telnet servers that are still running. As long as they're internal and properly secured from unauthorized access (which is very hard), it's **somewhat** okay.
9. Under what circumstances is this acceptable vs. negligent?
   1. I think in this circumstance it's somewhat acceptable. They put in place compensating controls to isolate it from outside networks. If there were no compensating controls or little response from leadership, it would be fairly negligent.
10. If TechNova were breached by a real attacker, should the leadership team face legal consequences? Why or why not?
    1. I mean, if they get breached, then they accepted that risk, so therefore they should face the consequences of that risk. They decided not to upgrade the server because they wanted to prioritize profits, so their profits can and should be in jeopardy as a result.
