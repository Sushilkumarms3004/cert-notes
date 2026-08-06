---
title: "Lab 5 - DNS Footprinting"
date: 2026-08-03
tags: [ceh, lab, footprinting, dns, nslookup, osint]
---

## What DNS footprinting is
DNS is the internet's phonebook - it translates a domain name into an IP address and back. In this lab I gathered DNS information about a target: its DNS servers, its DNS records, and the type of servers it uses. This data includes domain names, computer names, IP addresses, mail servers, and service records, which helps identify the key hosts on a network. Target used: certifiedhacker.com.

## Part 1 - nslookup command line
1. On the Windows 11 machine, opened Command Prompt and ran nslookup. This showed the default DNS server assigned to my machine.
2. Typed set type=a and pressed Enter. This tells nslookup to look up the IPv4 address (A record) of a domain.
3. Typed www.certifiedhacker.com. It resolved the IP. The answer was non-authoritative - it came from my local resolver (dns.google, 8.8.8.8) and not the server that actually hosts the domain. The IP returned was 162.241.216.11.
4. To find the domain's own name server, typed set type=cname then certifiedhacker.com. This returned the authoritative name server (ns1.bluehost.com) and the mail server (dnsadmin.box5331.bluehost.com).
5. To get the IP of that name server, typed set type=a again, then ns1.bluehost.com. This returned its IP address.

## Authoritative vs non-authoritative
- Non-authoritative: the answer came from my local resolver's cache (Google 8.8.8.8). Correct, but second-hand.
- Authoritative: the answer comes straight from the server that officially holds the domain's records - the source of truth.

An attacker who finds the authoritative (primary) name server and its IP could target it with DoS, DDoS, or URL redirection, since it holds all the domain's records.

## Part 2 - NSLOOKUP online tool
1. Opened Firefox and went to http://www.kloth.net/services/nslookup.php
2. In the Domain field, entered www.certifiedhacker.com, left Query as A (IPv4 address), and clicked Look it up.
3. Opened the Query dropdown, selected AAAA (IPv6 address), and looked that up too - worth checking because attacks are possible over IPv6 as well.

## Record types to remember
- A - domain to IPv4 address
- AAAA - domain to IPv6 address
- CNAME - an alias pointing one name to another
- NS - the name servers for the domain
- MX - the mail servers

## Other tools to try
- DNSdumpster - https://dnsdumpster.com for extra DNS information

## Lab answer
- Primary name server of www.certifiedhacker.com: ns1.bluehost.com
