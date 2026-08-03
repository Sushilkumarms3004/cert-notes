---
title: "Module 06 - System Hacking"
date: 2026-08-03
tags: [ceh, exploitation, privilege-escalation, metasploit]
---

## Key concepts
• System hacking goal - gain access, escalate privileges, maintain access, cover tracks
• Password attacks - dictionary, brute force, hybrid, rainbow tables
• Password cracking - offline (cracking captured hashes) vs online (guessing at login)
• Privilege escalation - vertical (user to admin) vs horizontal (user to another user)
• Hash types - Windows LM/NTLM, Linux stored in /etc/shadow
• Pass-the-hash - authenticating with the hash itself, no plaintext needed
• Steganography - hiding data inside images or files
• Covering tracks - clearing logs, timestomping, disabling auditing

## Commands / tools
• john --wordlist=rockyou.txt hashes.txt - John the Ripper offline cracking
• hashcat -m 1000 hashes.txt rockyou.txt - GPU cracking (mode 1000 = NTLM)
• hydra -l admin -P rockyou.txt ssh://target - online brute force
• responder - capture NTLM hashes on a LAN
• mimikatz - dump Windows credentials from memory
• msfconsole - Metasploit exploitation framework
• meterpreter: getuid, getsystem, hashdump, migrate
• crackmapexec smb target -u user -p pass - pass-the-hash and SMB

## Interview Q&A
**Q: Difference between vertical and horizontal privilege escalation?**
A: Vertical moves from a lower-privileged account to a higher one (user to admin/root). Horizontal moves sideways to another account at the same level to access their data.

**Q: What is a pass-the-hash attack?**
A: Instead of cracking a captured NTLM hash, the attacker uses the hash directly to authenticate, because Windows accepts the hash as proof of the password.

**Q: Online vs offline password cracking?**
A: Online guesses live against a login and is slow and detectable due to lockouts. Offline cracks captured hashes locally with no rate limit, so it is far faster.

**Q: Why do attackers clear logs and how do defenders counter it?**
A: To hide their activity and slow investigation. Defenders forward logs to a central SIEM in real time so a cleared local log is already stored elsewhere.

## Cert-relevant points
• System hacking spans phases 3-5: gaining access, maintaining access, covering tracks
• hashcat mode numbers appear in exams: 0 MD5, 1000 NTLM, 1800 sha512crypt
• Know John vs hashcat: John CPU-friendly, hashcat GPU-accelerated
• Rainbow tables are defeated by salting
• mimikatz + pass-the-hash are classic AD attack talking points

## Lab notes
• Practice cracking against lab accounts on Windows 11 (10.10.1.11) and Server 2019 (10.10.1.19)
• Metasploit and mimikatz available on the Parrot attacker box (10.10.1.13)
• Domain controller CEH.com on Server 2022 (10.10.1.22) for AD attacks
