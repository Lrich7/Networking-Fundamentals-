# Lab 17 — DNS Fundamentals

## Lab Objective

Query DNS records, inspect client DNS configuration, observe DNS traffic, and troubleshoot basic DNS failures.

---

# Part 1 — Inspect DNS Configuration

Run:

```powershell
Get-DnsClientServerAddress
```

Identify the DNS server entries for your active adapter without publishing internal addresses.

---

# Part 2 — Resolve a Name

Run:

```powershell
Resolve-DnsName example.com
```

Identify any returned:

```text
Name
Type
IPAddress
```

---

# Part 3 — Nslookup

Run:

```text
nslookup example.com
```

Compare the result with `Resolve-DnsName`.

---

# Part 4 — Record Types

Try safe public queries:

```powershell
Resolve-DnsName example.com -Type A
Resolve-DnsName example.com -Type AAAA
Resolve-DnsName example.com -Type NS
```

Availability of particular records varies.

---

# Part 5 — DNS Cache

Run:

```text
ipconfig /displaydns
```

Find an entry created during your testing if possible.

Do not paste a full company DNS cache into a public repository.

---

# Part 6 — Wireshark

Start a training capture and run:

```text
nslookup example.com
```

Filter:

```text
dns
```

Identify:

```text
Query
Response
Requested name
Record type
```

---

# Part 7 — Build Packet Tracer DNS

Create:

```text
PC ── Switch ── Server
```

Use a lab subnet such as:

```text
192.168.170.0/24
```

Configure the server with DNS service if supported.

Create a lab record such as:

```text
web.training.local → 192.168.170.20
```

Configure the client to use the DNS server.

---

# Part 8 — Test by IP and Name

Verify:

```text
Ping/service by IP
Ping/service by name
```

Document the difference.

---

# Part 9 — Break DNS

Give the client an incorrect DNS server address while leaving:

```text
IP
Mask
Gateway
```

correct.

Test by IP and name.

Record:

```text
IP test: __________________
Name test: ________________
Root cause: _______________
```

Repair it.

---

# Part 10 — Troubleshooting Ticket

> "The user can reach the server at 192.168.170.20, but `web.training.local` fails."

Document:

```text
Scope
IP test
DNS server
DNS query
Record
Root cause
Fix
Verification
```

---

# Knowledge Check

1. What record type maps to IPv4?
2. What record type maps to IPv6?
3. What tool can query DNS from PowerShell?
4. Why should you test by IP and by name separately?
5. What does DNS caching accomplish?

---

# Challenge

Build two DNS records in Packet Tracer and prove both resolve.

Then create two faults:

```text
Wrong client DNS server
Missing/incorrect DNS record
```

Diagnose each without changing unrelated IP settings.

Save:

```text
lab-17-dns-fundamentals.pkt
```

---

# Lab Completion Checklist

- [ ] Inspected DNS configuration
- [ ] Used Resolve-DnsName
- [ ] Used nslookup
- [ ] Queried record types
- [ ] Inspected DNS cache
- [ ] Observed DNS traffic
- [ ] Built Packet Tracer DNS
- [ ] Tested by IP and name
- [ ] Diagnosed wrong DNS server
- [ ] Completed troubleshooting ticket
- [ ] Completed knowledge check
- [ ] Completed challenge

---

# Lab Complete

You have completed **Lab 17 — DNS Fundamentals**.

# Next Lesson

➡️ **[Lesson 18 — DHCP Fundamentals](../lessons/lesson-18-dhcp-fundamentals.md)**
