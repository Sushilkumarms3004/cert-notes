---
title: "CCNA - OSI Model and TCP/IP"
date: 2026-08-03
tags: [ccna, networking, osi]
---

## OSI layers (7 to 1)
• 7 Application - user-facing protocols: HTTP, FTP, DNS, SMTP
• 6 Presentation - encryption, compression, encoding (SSL/TLS, JPEG)
• 5 Session - sets up, manages, tears down sessions
• 4 Transport - TCP and UDP, ports, segmentation, reliability
• 3 Network - IP addressing and routing, routers, packets
• 2 Data Link - MAC addressing, switches, frames, ARP
• 1 Physical - cables, signals, bits, NICs, hubs

Mnemonic: All People Seem To Need Data Processing

## TCP/IP model (4 layers)
• Application - maps to OSI layers 7, 6, 5
• Transport - maps to OSI layer 4
• Internet - maps to OSI layer 3
• Network Access - maps to OSI layers 2 and 1

## PDU names per layer
• Layer 4 - Segment (TCP) / Datagram (UDP)
• Layer 3 - Packet
• Layer 2 - Frame
• Layer 1 - Bits

## TCP vs UDP
• TCP - connection oriented, three-way handshake, reliable, ordered, slower. Used by HTTP, HTTPS, FTP, SSH, SMTP
• UDP - connectionless, no handshake, no guarantee, faster. Used by DNS, DHCP, TFTP, VoIP, streaming

## Interview Q&A
**Q: At which layer does a router operate, and a switch?**
A: Router at layer 3 using IP addresses. Switch at layer 2 using MAC addresses. Layer 3 switches can do both.

**Q: What is encapsulation?**
A: Each layer adds its own header as data moves down the stack - data becomes segment, then packet, then frame, then bits. Decapsulation strips them off on the receiving side.

**Q: Why does DNS mostly use UDP?**
A: Queries are small and speed matters more than reliability. If a response is lost the client just retries. DNS switches to TCP for zone transfers and responses over 512 bytes.

**Q: Which layer does a firewall work at?**
A: Depends on type. Packet-filtering firewalls at layer 3 and 4; next-gen and application firewalls inspect up to layer 7.

## Exam-relevant points
• Know layer numbers both directions - questions phrase it either way
• Know which device sits at which layer: hub L1, switch L2, router L3, firewall L3-L7
• PDU names are commonly tested - segment, packet, frame, bits
• Map every protocol you learn to its layer and port number
