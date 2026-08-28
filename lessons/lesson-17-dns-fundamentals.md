# Lesson 17 — DNS Fundamentals

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain the purpose of DNS.
- Describe the basic DNS resolution process.
- Recognize common DNS record types.
- Explain recursive and authoritative DNS roles at a beginner level.
- Explain DNS caching.
- Use Windows and PowerShell DNS troubleshooting tools.
- Distinguish DNS failures from general IP connectivity failures.
- Build and troubleshoot basic DNS in Packet Tracer.

---

# What Is DNS?

**Domain Name System (DNS)** translates names into information such as IP addresses.

Instead of remembering:

```text
93.184.216.x
```

users can work with names such as:

```text
example.com
```

DNS is one of the most important infrastructure services on modern networks.

---

# Basic Resolution Process

Simplified:

```text
User enters hostname
       ↓
Client checks local information/cache
       ↓
Configured DNS resolver
       ↓
DNS hierarchy / authoritative information
       ↓
Answer returned
       ↓
Client connects to destination IP
```

---

# DNS Hierarchy

DNS is hierarchical.

Conceptually:

```text
Root
 ↓
Top-Level Domain
 ↓
Domain
 ↓
Host / Record
```

Example:

```text
www.example.com
```

---

# Common Record Types

## A

Maps a name to an IPv4 address.

```text
server.example.com → 192.0.2.10
```

## AAAA

Maps a name to an IPv6 address.

## CNAME

Creates an alias pointing to another DNS name.

## MX

Identifies mail servers for a domain.

## NS

Identifies authoritative name servers.

## PTR

Used for reverse lookup information.

## TXT

Stores text data and is commonly used for verification and email/security-related records.

---

# DNS Ports

DNS commonly uses:

```text
UDP 53
TCP 53
```

Do not memorize DNS as UDP-only.

---

# DNS Cache

Clients and resolvers cache answers to reduce repeated queries.

Windows:

```text
ipconfig /displaydns
```

Clear the local resolver cache:

```text
ipconfig /flushdns
```

Use cache-clearing carefully during troubleshooting because it changes the current state.

---

# Windows DNS Tools

PowerShell:

```powershell
Resolve-DnsName example.com
```

Command Prompt:

```text
nslookup example.com
```

Inspect configuration:

```powershell
Get-DnsClientServerAddress
```

---

# DNS vs. Connectivity

Scenario:

```text
ping 8.8.8.8
    Works

Resolve-DnsName example.com
    Fails
```

This strongly suggests you should investigate name resolution rather than immediately blaming the physical network.

---

# Wrong DNS Server

A client can have:

```text
Correct IP
Correct subnet
Correct gateway
Wrong DNS server
```

Result:

```text
IP connectivity may work
Names may fail
```

---

# DNS Troubleshooting Flow

```text
IP configuration valid?
       ↓
Gateway/remote IP reachable?
       ↓
DNS server configured?
       ↓
DNS server reachable?
       ↓
Query specific record
       ↓
Compare another resolver if authorized
       ↓
Check cache / record / server
```

---

# Key Terms

```text
DNS
Resolver
Authoritative Server
A
AAAA
CNAME
MX
NS
PTR
TXT
Cache
Forward Lookup
Reverse Lookup
```

---

# Knowledge Check

1. What problem does DNS solve?
2. Which record maps a name to IPv4?
3. Which record maps a name to IPv6?
4. Which port does DNS commonly use?
5. What does a CNAME do?
6. Why can IP connectivity work while names fail?

---

# Hands-On Lab

➡️ **[Lab 17 — DNS Fundamentals](../labs/lab-17-dns-fundamentals.md)**
