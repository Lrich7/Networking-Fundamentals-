# 🧪 Lab 15 — DNS

Welcome to **Lab 15 of Networking Fundamentals**.

This lab starts with your real Windows computer.

Instead of immediately building another Packet Tracer topology, you'll inspect the DNS configuration and traffic your computer actually uses.

Then you'll move into Packet Tracer where you can safely:

> **Break DNS on purpose.**

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Identify configured DNS servers
- Use `nslookup`
- Use `Resolve-DnsName`
- Query different DNS record types
- Perform forward lookups
- Perform reverse lookups
- Inspect the Windows DNS cache
- Understand DNS TTL
- Capture DNS traffic in Wireshark
- Identify DNS queries and responses
- Identify DNS UDP/TCP ports
- Compare DNS and application traffic
- Configure a Packet Tracer DNS server
- Create DNS A records
- Configure clients to use DNS
- Troubleshoot incorrect DNS servers
- Troubleshoot incorrect DNS records
- Distinguish DNS failures from IP/routing failures

---

# 🎓 Network+ Focus

This lab reinforces:

- DNS
- UDP/TCP 53
- A
- AAAA
- CNAME
- MX
- PTR
- NS
- TXT
- Forward lookup
- Reverse lookup
- DNS cache
- TTL
- DNS troubleshooting

---

# ⏱️ Estimated Time

**75–90 minutes**

---

# ⚠️ Safety

The Windows portion of this lab primarily uses read-only commands.

Do not:

- Change company DNS settings without authorization
- Disable production DNS
- Change network adapter configuration
- Capture other users' traffic without permission

Your personal Wireshark capture may contain:

- IP addresses
- DNS queries
- Hostnames
- Network information

> **Do not upload personal `.pcapng` captures to the public GitHub repository.**

---

# 🖥️ PART 1 — IDENTIFY YOUR DNS SERVER

Open:

> **Command Prompt**

Run:

```text
ipconfig /all
```

Find your active:

```text
Ethernet
```

or:

```text
Wi-Fi
```

adapter.

Locate:

```text
DNS Servers
```

Record:

```text
Adapter:

________________________________


IPv4 Address:

________________________________


Default Gateway:

________________________________


Primary DNS Server:

________________________________


Additional DNS Server:

________________________________
```

---

# 🧠 Question

Is your DNS server address:

```text
Same as your gateway?
```

or:

```text
Different?
```

Record:

```text
________________________________
```

Either can occur depending on the network design.

---

# ⚡ PART 2 — CHECK DNS WITH POWERSHELL

Open PowerShell.

Run:

```text
Get-DnsClientServerAddress
```

Find the active interface.

Record:

```text
Interface:

________________________________


DNS Server Address(es):

________________________________
```

---

# 🔎 PART 3 — BASIC NSLOOKUP

Run:

```text
nslookup example.com
```

Record:

```text
DNS Server Used:

________________________________


DNS Server Address:

________________________________


Resolved Address(es):

________________________________
```

---

# 🧠 What Just Happened?

Conceptually:

```text
YOUR PC
   │
   │ DNS Query
   ▼
DNS RESOLVER
   │
   │ DNS Response
   ▼
YOUR PC
```

Your computer asked:

> **What address information exists for example.com?**

---

# ⚡ PART 4 — RESOLVE-DNSNAME

Run:

```text
Resolve-DnsName example.com
```

Look for fields such as:

```text
Name
Type
TTL
IPAddress
```

Record one result:

```text
Name:

________________________________


Record Type:

________________________________


TTL:

________________________________


IP Address:

________________________________
```

---

# 🧠 TTL

Remember:

```text
TTL
=
Time To Live
```

It helps determine how long DNS information may remain cached.

---

# 🅰️ PART 5 — QUERY AN A RECORD

Run:

```text
Resolve-DnsName example.com -Type A
```

Record:

```text
IPv4 Address:

________________________________
```

What record type maps a name to IPv4?

> **A**

---

# 🅰️🅰️🅰️🅰️ PART 6 — QUERY AAAA

Run:

```text
Resolve-DnsName example.com -Type AAAA
```

If an AAAA record exists, record:

```text
IPv6 Address:

________________________________
```

If no AAAA record is returned, that is okay.

What does AAAA represent?

> **IPv6**

---

# ✉️ PART 7 — QUERY MX

Use a domain known to receive email, such as:

```text
gmail.com
```

Run:

```text
Resolve-DnsName gmail.com -Type MX
```

Record one mail exchanger:

```text
________________________________
```

---

# 🧠 MX

Remember:

```text
MX
=
Mail Exchange
```

It identifies systems responsible for receiving mail for a domain.

---

# 🗺️ PART 8 — QUERY NS

Run:

```text
Resolve-DnsName example.com -Type NS
```

Record one name server:

```text
________________________________
```

NS means:

> **Name Server**

---

# 📝 PART 9 — QUERY TXT

Run:

```text
Resolve-DnsName example.com -Type TXT
```

If TXT records are returned, inspect them.

You do not need to copy long TXT values.

Record:

```text
TXT Record Present?

YES / NO
```

---

# 🔙 PART 10 — REVERSE LOOKUP

Run:

```text
nslookup 8.8.8.8
```

Then try:

```text
Resolve-DnsName 8.8.8.8
```

Record any returned name:

```text
________________________________
```

---

# 🧠 What Record Is Involved?

Reverse DNS commonly uses:

> **PTR**

---

# 📋 PART 11 — RECORD TYPE REVIEW

Complete:

| Record | Purpose |
|---|---|
| A | |
| AAAA | |
| CNAME | |
| MX | |
| PTR | |
| NS | |
| TXT | |

Answers:

| Record | Purpose |
|---|---|
| A | Name → IPv4 |
| AAAA | Name → IPv6 |
| CNAME | Alias |
| MX | Mail server |
| PTR | Reverse DNS |
| NS | Name server |
| TXT | Text/policy/verification data |

---

# 💾 PART 12 — VIEW WINDOWS DNS CACHE

Run:

```text
ipconfig /displaydns
```

Look through the output.

You may see cached information containing:

```text
Record Name
Record Type
Time To Live
Data Length
```

---

# 🧠 Why Is It There?

Your computer can cache DNS information to avoid performing unnecessary repeated lookups.

Conceptually:

```text
First Lookup
     ↓
DNS Server
     ↓
Answer
     ↓
Cache
```

Later:

```text
Same Lookup
     ↓
Cached Answer
```

until the cached information expires or is cleared.

---

# 🧹 PART 13 — DNS CACHE COMMAND

The Windows command to clear the DNS resolver cache is:

```text
ipconfig /flushdns
```

You do **not** need to run this on a managed work computer just to complete the lab.

Record:

```text
Command:

ipconfig ___________________
```

Answer:

```text
/flushdns
```

---

# 🦈 PART 14 — OPEN WIRESHARK

Open:

> **Wireshark**

Select your active:

```text
Ethernet
```

or:

```text
Wi-Fi
```

interface.

Start capturing.

---

# 🔍 PART 15 — DNS FILTER

Use:

```text
dns
```

as the display filter.

---

# 🔄 PART 16 — GENERATE A DNS QUERY

While Wireshark is capturing, run:

```text
nslookup example.com
```

Return to Wireshark.

Look for DNS traffic.

---

# 📝 Record

Select a DNS query.

Record:

```text
Source IP:

________________________________


Destination IP:

________________________________


Protocol:

________________________________


Queried Name:

________________________________
```

---

# 📡 PART 17 — INSPECT TRANSPORT

Expand the packet details.

Look for:

```text
User Datagram Protocol
```

or, depending on the query:

```text
Transmission Control Protocol
```

Record:

```text
Transport Protocol:

________________________________


Source Port:

________________________________


Destination Port:

________________________________
```

For traditional DNS, the destination is commonly:

```text
53
```

---

# 🔁 PART 18 — FIND THE RESPONSE

Find the corresponding DNS response.

Record:

```text
Source IP:

________________________________


Destination IP:

________________________________


Answer:

________________________________
```

Notice:

```text
Query
PC → DNS Server
```

then:

```text
Response
DNS Server → PC
```

---

# 🧠 DNS PORT REVIEW

Remember:

```text
DNS
=
UDP 53
and
TCP 53
```

Many simple queries commonly use UDP.

---

# 🔐 PART 19 — IF YOU DON'T SEE DNS

You may not see the expected traditional DNS traffic.

Possible reasons include:

- Cached DNS information
- Encrypted DNS
- Different interface selected
- VPN
- Browser-specific DNS behavior
- Query occurred before capture started

Using:

```text
nslookup
```

rather than only opening a browser can make traditional DNS testing easier.

---

# 🌐 PART 20 — DNS THEN APPLICATION TRAFFIC

Start a fresh capture if desired.

Run:

```text
nslookup example.com
```

Then visit:

```text
https://example.com
```

in your browser.

Observe the difference between:

```text
DNS
```

and later traffic such as:

```text
TCP
TLS
QUIC
```

depending on your browser and network.

---

# ⭐ Key Concept

DNS answers:

> **Where is the service?**

Protocols such as HTTPS handle:

> **Communication with the service.**

---

# 🧪 PART 21 — DNS TROUBLESHOOTING TEST

Run:

```text
nslookup example.com
```

Then:

```text
ping 8.8.8.8
```

These test different things.

Complete:

```text
nslookup
primarily tests:

________________________________


ping 8.8.8.8
primarily tests:

________________________________
```

Answers:

```text
DNS name resolution

IP/ICMP reachability
```

---

# ⚠️ Important

Do not use:

```text
ping example.com
```

as your only DNS test.

It combines:

```text
DNS Resolution
+
ICMP Reachability
```

Use a DNS-specific tool when testing DNS.

---

# 💾 PART 22 — STOP THE CAPTURE

Stop Wireshark.

If you save it, use something such as:

```text
lab-15-dns.pcapng
```

Keep it:

> **Local**

Do not upload personal packet captures to the public repository.

---

# 🏗️ PART 23 — PACKET TRACER DNS NETWORK

Now open:

> **Cisco Packet Tracer**

Build:

```text
PC-01
   │
   ▼
 SW-01
   │
   ▼
 R-01
   │
   ▼
 SW-02
   │
   ├──── DNS-01
   │
   └──── WEB-01
```

---

# 🌐 Network Plan

## Client Network

```text
192.168.10.0/24
```

## Server Network

```text
192.168.20.0/24
```

---

# 📋 Addressing

| Device | Address | Gateway |
|---|---|---|
| PC-01 | 192.168.10.10/24 | 192.168.10.1 |
| R-01 Client Interface | 192.168.10.1/24 | — |
| R-01 Server Interface | 192.168.20.1/24 | — |
| DNS-01 | 192.168.20.10/24 | 192.168.20.1 |
| WEB-01 | 192.168.20.20/24 | 192.168.20.1 |

---

# 🔀 PART 24 — CONFIGURE R-01

On R-01:

```text
enable
```

```text
configure terminal
```

Configure the client-facing interface.

Example:

```text
interface gigabitethernet 0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
exit
```

Configure the server-facing interface:

```text
interface gigabitethernet 0/1
ip address 192.168.20.1 255.255.255.0
no shutdown
end
```

---

# 🔍 Verify

```text
show ip interface brief
```

Both interfaces should be:

```text
up
up
```

---

# 🖥️ PART 25 — CONFIGURE PC-01

Configure:

```text
IP:
192.168.10.10

Mask:
255.255.255.0

Gateway:
192.168.10.1

DNS:
192.168.20.10
```

---

# 🗄️ PART 26 — CONFIGURE DNS-01

Configure:

```text
IP:
192.168.20.10

Mask:
255.255.255.0

Gateway:
192.168.20.1
```

---

# 🌐 PART 27 — CONFIGURE WEB-01

Configure:

```text
IP:
192.168.20.20

Mask:
255.255.255.0

Gateway:
192.168.20.1
```

Go to:

```text
Services
   ↓
HTTP
```

Make sure HTTP is:

> **On**

---

# 🧪 PART 28 — VERIFY IP BEFORE DNS

From PC-01:

```text
ping 192.168.10.1
```

Then:

```text
ping 192.168.20.10
```

Then:

```text
ping 192.168.20.20
```

Do not continue until IP connectivity works.

---

# ⭐ Why Test IP First?

Because DNS depends on:

```text
Working IP Configuration
        +
Working Routing
```

If PC-01 cannot reach:

```text
192.168.20.10
```

then DNS cannot work regardless of whether the DNS service is configured correctly.

---

# 🗂️ PART 29 — ENABLE DNS

On DNS-01:

```text
Services
   ↓
DNS
```

Turn DNS:

> **On**

Create an A record:

```text
Name:
www.training.local

Address:
192.168.20.20
```

Add/save the record.

---

# 🔎 PART 30 — TEST DNS

On PC-01:

```text
nslookup www.training.local
```

if supported by the Packet Tracer client.

You should receive:

```text
192.168.20.20
```

---

# 🌐 PART 31 — TEST THE WEBSITE BY NAME

Open PC-01's web browser.

Enter:

```text
http://www.training.local
```

The Packet Tracer web page should load.

---

# 🏆 Major Checkpoint

You now have:

```text
PC-01
   │
   │ DNS Query
   ▼
DNS-01
   │
   │ www.training.local
   │ = 192.168.20.20
   ▼
PC-01
   │
   │ HTTP
   ▼
WEB-01
```

---

# 🔬 PART 32 — SIMULATION MODE

Switch to:

> **Simulation Mode**

Filter for:

```text
DNS
```

and, if desired:

```text
HTTP
TCP
```

Generate a new request for:

```text
www.training.local
```

Observe:

```text
DNS Query
      ↓
DNS Response
      ↓
HTTP Communication
```

---

# 💥 PART 33 — BREAK DNS SERVICE

On DNS-01:

```text
Services
   ↓
DNS
```

Turn DNS:

> **Off**

---

# 🧪 Test by Name

From PC-01 try:

```text
www.training.local
```

Expected:

> **Failure**

---

# 🧪 Test by IP

Try:

```text
http://192.168.20.20
```

Expected:

> **Success**

---

# 🧠 What Does This Prove?

```text
IP Connectivity
✅

Web Service
✅

DNS
❌
```

That is an extremely useful troubleshooting pattern.

---

# 🔧 Repair

Turn DNS:

> **On**

Retest by name.

---

# 💥 PART 34 — WRONG DNS SERVER

Change PC-01's DNS server from:

```text
192.168.20.10
```

to:

```text
192.168.20.99
```

---

# 🧪 Test

Try:

```text
http://www.training.local
```

Then:

```text
http://192.168.20.20
```

Record:

```text
Hostname Works?

YES / NO


Direct IP Works?

YES / NO
```

Expected:

```text
Hostname:
NO

Direct IP:
YES
```

---

# 🧠 Root Cause

The client is configured with:

> **The wrong DNS server**

This is a client configuration problem, not a web-server problem.

---

# 🔧 Repair

Restore:

```text
DNS:
192.168.20.10
```

---

# 💥 PART 35 — WRONG DNS RECORD

On DNS-01, change:

```text
www.training.local
```

from:

```text
192.168.20.20
```

to:

```text
192.168.20.99
```

---

# 🧪 Test

Resolve:

```text
www.training.local
```

What happens?

DNS may successfully respond with:

```text
192.168.20.99
```

But the website won't work.

---

# ⭐ Important

This demonstrates:

```text
DNS Service
✅

DNS Response
✅

DNS DATA
❌
```

A DNS server responding does not mean:

> **The DNS record is correct.**

---

# 🔧 Repair

Restore:

```text
www.training.local
→
192.168.20.20
```

---

# 💥 PART 36 — BREAK ROUTING

Disable R-01's server-facing interface:

```text
configure terminal
```

```text
interface gigabitethernet 0/1
```

```text
shutdown
```

---

# 🧪 Test

From PC-01:

```text
ping 192.168.20.10
```

Then try:

```text
www.training.local
```

Both should fail.

---

# 🧠 Is DNS the Root Cause?

No.

The actual problem is:

> **Layer 3 connectivity to the DNS server**

This is why troubleshooting should work from lower layers upward.

---

# 🔧 Repair

```text
no shutdown
```

Then verify:

```text
show ip interface brief
```

Retest.

---

# 💥 PART 37 — WEB SERVICE FAILURE

Leave DNS working.

On WEB-01:

```text
Services
   ↓
HTTP
```

Turn HTTP:

> **Off**

---

# 🔎 Test DNS

Resolve:

```text
www.training.local
```

Expected:

> **Success**

---

# 🌐 Test Website

Try:

```text
http://www.training.local
```

Expected:

> **Failure**

---

# 🧠 What Does This Prove?

```text
DNS
✅

IP Connectivity
✅

Application Service
❌
```

Do not blame DNS simply because:

> "The website doesn't load."

---

# 🔧 Repair

Turn HTTP:

> **On**

---

# 🛠️ PART 38 — TROUBLESHOOTING BY SCOPE

Consider these situations.

## Scenario A

```text
No names resolve
```

Investigate:

- Client DNS configuration
- DNS server availability
- Network path
- DNS service

## Scenario B

```text
Most names resolve
but one name doesn't
```

Investigate:

- Missing record
- Incorrect record
- Typo
- Record-specific problem

## Scenario C

```text
Name resolves correctly
but application fails
```

Investigate:

- Application service
- Port
- Firewall
- Routing
- Server

---

# 🧭 PART 39 — DNS TROUBLESHOOTING FLOW

Use:

```text
Does Client Have Valid IP?
        ↓
Can Client Reach Gateway?
        ↓
Which DNS Server Is Configured?
        ↓
Can Client Reach DNS Server?
        ↓
Does DNS Query Receive Response?
        ↓
Is Returned Record Correct?
        ↓
Does Direct IP Work?
        ↓
Does Application Work?
```

---

# 📝 PART 40 — TROUBLESHOOTING REPORT

A user reports:

> "I can't open www.training.local."

Document:

```text
Problem:

________________________________


Client IP:

________________________________


Default Gateway:

________________________________


DNS Server:

________________________________


Can Client Reach Gateway?

YES / NO


Can Client Reach DNS Server?

YES / NO


Does nslookup Work?

YES / NO


Returned Address:

________________________________


Is Returned Address Correct?

YES / NO


Does Direct IP Work?

YES / NO


Is HTTP Running?

YES / NO


Root Cause:

________________________________


Solution:

________________________________


Verification:

________________________________
```

---

# 🧠 Knowledge Check

### 1.

What does DNS stand for?

### 2.

Which record maps a name to IPv4?

### 3.

Which record maps a name to IPv6?

### 4.

Which record is an alias?

### 5.

Which record identifies mail servers?

### 6.

Which record supports reverse DNS?

### 7.

What port does DNS use?

### 8.

Which Windows command queries DNS?

### 9.

Which command displays the Windows DNS cache?

### 10.

If direct IP works but the hostname fails, what service should you investigate?

---

# ✅ Answers

1. **Domain Name System**
2. **A**
3. **AAAA**
4. **CNAME**
5. **MX**
6. **PTR**
7. **53**
8. **`nslookup`**
9. **`ipconfig /displaydns`**
10. **DNS**

---

# 🎓 Network+ Challenge 1

A user can access:

```text
http://192.168.20.20
```

but not:

```text
http://www.training.local
```

What should you investigate?

> **DNS**

---

# 🎓 Network+ Challenge 2

`nslookup` returns:

```text
www.training.local
192.168.20.99
```

but the actual server is:

```text
192.168.20.20
```

What is wrong?

> **The DNS record contains incorrect data.**

---

# 🎓 Network+ Challenge 3

Which record would you query to find the IPv6 address for a hostname?

> **AAAA**

---

# 🎓 Network+ Challenge 4

Which record would you query to identify the mail server for a domain?

> **MX**

---

# 🎓 Network+ Challenge 5

Which port should you remember for DNS?

> **53 — UDP and TCP**

---

# 🎓 Network+ Challenge 6

A DNS query works, but HTTPS to the returned server fails.

Does that prove DNS is broken?

> **No. DNS may be functioning correctly while the application, port, firewall, or server has a problem.**

---

# 📋 Lab Review

In this lab, you:

- Identified your real DNS servers
- Used `ipconfig /all`
- Used `Get-DnsClientServerAddress`
- Used `nslookup`
- Used `Resolve-DnsName`
- Queried A records
- Queried AAAA records
- Queried MX records
- Queried NS records
- Examined TXT records
- Performed reverse DNS
- Reviewed PTR records
- Examined the Windows DNS cache
- Reviewed TTL
- Learned `ipconfig /flushdns`
- Captured DNS in Wireshark
- Identified DNS queries
- Identified DNS responses
- Reviewed UDP/TCP 53
- Compared DNS with application traffic
- Built an internal DNS environment
- Created an A record
- Resolved an internal hostname
- Accessed a web server by name
- Broke the DNS service
- Tested direct IP vs hostname
- Troubleshot a wrong DNS server
- Troubleshot an incorrect DNS record
- Distinguished routing failures from DNS failures
- Distinguished application failures from DNS failures

---

# 💾 Save Your Files

Packet Tracer:

```text
lab-15-dns.pkt
```

Optional local Wireshark capture:

```text
lab-15-dns.pcapng
```

Keep personal packet captures:

> **Local only**

You don't need to upload either completed lab file to the public repository.

---

# 🏆 Lab Complete

You can now break a user's:

> "The Internet doesn't work"

report into much more useful questions:

```text
Does the device have an IP?
        ↓
Can it reach the gateway?
        ↓
Can it reach the DNS server?
        ↓
Can DNS resolve the name?
        ↓
Is the returned address correct?
        ↓
Can the client reach that address?
        ↓
Is the application/service working?
```

Instead of treating DNS as mysterious, you can test each dependency separately.

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ COMPLETE

🔵 PHASE 2 — ADDRESSING & COMMUNICATION
✅ COMPLETE

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES

✅ Lesson 11 — Switching Fundamentals
✅ Lab 11

✅ Lesson 12 — VLANs & Network Segmentation
✅ Lab 12

✅ Lesson 13 — Routing Fundamentals
✅ Lab 13

✅ Lesson 14 — DHCP
✅ Lab 14

✅ Lesson 15 — DNS
✅ Lab 15

        ↓

🟡 NEXT:
Lesson 16 — NAT & Address Translation

⬜ Lab 16 — NAT & Address Translation

        ↓

🏗️ Project 03
Build a Routed Small-Business Network
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 16 — NAT & Address Translation**

So far we've built networks using private addresses such as:

```text
192.168.10.0/24
192.168.20.0/24
10.0.0.0/30
```

But private IPv4 addresses aren't normally routed across the public Internet.

So how can hundreds of internal devices using private addresses access outside networks through a much smaller number of public IPv4 addresses?

That's where:

> **NAT — Network Address Translation**

comes in.

Lesson 16 will cover:

- NAT
- Private vs. public IPv4
- Inside vs. outside
- Static NAT
- Dynamic NAT
- PAT
- NAT overload
- Inside local addresses
- Inside global addresses
- Port translation
- NAT tables
- NAT troubleshooting
- Cisco NAT configuration
- How NAT fits into small-business Internet access

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**