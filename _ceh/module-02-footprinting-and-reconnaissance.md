---
title: "Module 02 - Footprinting and Reconnaissance"
tags: [ceh, recon, osint]
---

## Key concepts
• Footprinting - collecting information about a target before attacking
• Passive recon - no direct contact with target (WHOIS, Google, social media)
• Active recon - direct interaction with target (ping, traceroute, port scan)
• Attack surface - all points where an attacker could try to get in
• Google Dorking - using advanced search operators to find exposed data

## Commands / tools
• whois example.com - domain owner, registrar, name servers
• nslookup example.com - resolve domain to IP
• dig example.com ANY - detailed DNS records
• theHarvester -d example.com -b google - collect emails and subdomains
• site:example.com filetype:pdf - Google dork for exposed files
• Recon-ng, Maltego, Shodan - OSINT frameworks and search engines

## Interview Q&A
**Q: Difference between active and passive reconnaissance?**
A: Passive gathers info without touching the target (public records, search engines). Active sends traffic to the target (scanning, pinging) and can be logged or detected.

**Q: Why is footprinting the first phase of hacking?**
A: It builds the target picture - IPs, domains, employees, tech stack - so later phases are focused instead of blind.

**Q: What can WHOIS reveal?**
A: Registrar, registration and expiry dates, name servers, and sometimes contact details if not privacy-protected.

## Cert-relevant points
• Know the 7 footprinting types: search engines, web services, social networking, website, email, WHOIS, DNS, network
• CEH tests the passive vs active distinction heavily - passive leaves no trace on the target
• Countermeasures: enable WHOIS privacy, restrict info in job postings, limit DNS zone transfers
