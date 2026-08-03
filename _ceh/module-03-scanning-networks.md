---
title: "Module 03 - Scanning Networks"
tags: [ceh, nmap, scanning]
---

## Key concepts
• Network scanning - finding live hosts, open ports, and running services
• Port states - open, closed, filtered (firewall blocking)
• TCP three-way handshake - SYN, SYN-ACK, ACK
• Banner grabbing - reading service response to identify software and version
• IDS evasion - fragmentation, decoys, timing to avoid detection

## Commands / tools
• nmap -sn 10.10.1.0/24 - ping sweep, find live hosts only
• nmap -sS target - SYN stealth scan (half-open, does not complete handshake)
• nmap -sT target - full TCP connect scan (noisy, logged)
• nmap -sU target - UDP scan (slow)
• nmap -sV target - service and version detection
• nmap -O target - OS fingerprinting
• nmap -A target - aggressive: OS + version + scripts + traceroute
• nmap -p- target - scan all 65535 ports
• nmap -T4 target - faster timing template
• nmap -D RND:10 target - decoy scan to hide real source
• Hping3, Angry IP Scanner, Netcat - alternative scanning tools

## Interview Q&A
**Q: Why is a SYN scan called stealth?**
A: It sends SYN, gets SYN-ACK, then sends RST instead of ACK. The connection never completes, so older systems may not log it.

**Q: How do you tell a closed port from a filtered port?**
A: Closed replies with RST. Filtered gives no reply at all, or an ICMP unreachable - a firewall is dropping the probe.

**Q: Why is UDP scanning slower than TCP?**
A: UDP is connectionless with no handshake, so nmap must wait for timeouts to infer state, and rate limiting slows it further.

## Cert-relevant points
• Memorize nmap flags - CEH asks which flag does what, very frequently
• SYN = -sS, Connect = -sT, UDP = -sU, Version = -sV, OS = -O
• Know the flag combinations in Xmas (-sX), NULL (-sN), FIN (-sF) scans
• Countermeasures: firewall rules, IDS/IPS, disabling unused ports and services
