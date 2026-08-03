---
title: "Module 04 - Enumeration"
date: 2026-08-03
tags: [ceh, enumeration, smb, snmp]
---

## Key concepts
• Enumeration - actively connecting to a service to extract usernames, shares, groups, and machine names
• Difference from scanning - scanning finds open ports, enumeration extracts detail from those services
• Null session - connecting to SMB with no username or password on older Windows
• Banner grabbing - reading service version strings for known vulnerabilities
• SNMP community strings - default public (read) and private (read/write)
• LDAP enumeration - pulling Active Directory users, groups, and OUs

## Commands / tools
• enum4linux -a 10.10.1.22 - full SMB enumeration of a Windows host
• smbclient -L //10.10.1.22 -N - list shares with a null session
• nmap --script smb-enum-users,smb-enum-shares -p445 target
• snmpwalk -v2c -c public 10.10.1.22 - walk the SNMP tree
• ldapsearch -x -h 10.10.1.22 -b "dc=CEH,dc=com" - LDAP query
• nbtstat -A 10.10.1.11 - NetBIOS name table (Windows)
• net view \\\\10.10.1.22 - list shares from Windows CLI
• rpcclient -U "" 10.10.1.22 - null session RPC enumeration
• dnsrecon -d domain.com - DNS enumeration

## Interview Q&A
**Q: What is enumeration and how does it differ from scanning?**
A: Scanning tells you which ports and services are open. Enumeration goes a step further and actively queries those services to pull usernames, shares, group memberships, and system details.

**Q: What is a null session and why is it dangerous?**
A: An unauthenticated SMB connection using a blank username and password. On misconfigured legacy Windows it lets an attacker list users, shares, and password policy without credentials.

**Q: Why are default SNMP community strings a problem?**
A: Devices ship with public and private. If left unchanged, anyone can read the full device config, and private even allows writes to change it.

**Q: Which ports matter most for enumeration?**
A: 53 DNS, 135 and 139 and 445 SMB/NetBIOS/RPC, 161 SNMP, 389 LDAP, 25 SMTP.

## Cert-relevant points
• Enumeration follows scanning - still inside phase 2 before gaining access
• Memorise the enumeration ports: 53, 135, 139, 445, 161, 389, 25
• SNMP defaults public and private come up repeatedly in exams
• enum4linux is the go-to all-in-one SMB tool in labs

## Lab notes
• Server 2022 (10.10.1.22) is the domain controller for CEH.com - best LDAP and SMB target
• Run enumeration from Parrot at 10.10.1.13
• Domain accounts available in lab for testing authenticated enumeration
