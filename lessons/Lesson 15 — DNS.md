# 📘 Lesson 15 — DNS

Welcome to **Lesson 15 of Networking Fundamentals**.

In Lesson 14, DHCP automatically provided clients with:

```text
IP Address
Subnet Mask
Default Gateway
DNS Server
```

We understand the first three.

Now we need to answer:

> **Why does a computer need a DNS server?**

People prefer names such as:

```text
www.example.com
```

Computers ultimately need network addresses such as:

```text
93.184.216.34
```

DNS helps connect those two worlds.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain what DNS does
- Explain DNS name resolution
- Understand DNS clients and resolvers
- Understand recursive DNS servers
- Understand authoritative DNS servers
- Explain the DNS hierarchy
- Understand root DNS servers
- Understand top-level domains
- Explain DNS zones
- Understand common DNS record types
- Explain A and AAAA records
- Explain CNAME records
- Explain MX records
- Explain PTR records
- Explain NS records
- Explain TXT records
- Understand forward and reverse lookups
- Understand DNS caching
- Understand TTL
- Identify DNS ports
- Explain why DNS uses both UDP and TCP
- Use `nslookup`
- Use `Resolve-DnsName`
- Use `ipconfig /displaydns`
- Use `ipconfig /flushdns`
- Recognize common DNS failures
- Troubleshoot DNS systematically

---

# 🎓 Network+ Focus

For **CompTIA Network+ N10-009**, pay particular attention to:

- DNS
- Name resolution
- DNS servers
- DNS records
- A
- AAAA
- CNAME
- MX
- PTR
- NS
- TXT
- Forward lookup
- Reverse lookup
- DNS caching
- TTL
- UDP 53
- TCP 53
- DNS troubleshooting

One of the most important troubleshooting patterns is:

```text
IP Communication Works
        +
Hostname Communication Fails
        ↓
Investigate DNS
```

---

# 🌐 What Is DNS?

DNS stands for:

> **Domain Name System**

DNS provides a distributed naming system used to associate names with information such as IP addresses.

For example:

```text
www.example.com
        ↓
DNS
        ↓
IP Address
```

Without DNS, users would often need to remember IP addresses instead of names.

---

# 🧠 DNS Is Like a Directory

A simplified analogy is:

```text
Name
        ↓
DNS
        ↓
Address
```

Similar to looking up:

```text
Person's Name
        ↓
Contact List
        ↓
Phone Number
```

DNS helps applications locate network resources by name.

---

# ⭐ Important

DNS does **not** carry your normal web traffic.

DNS helps determine where the service is.

After resolution:

```text
Browser
   ↓
DNS Lookup
   ↓
IP Address Learned
   ↓
Browser Connects to Web Server
```

The actual web connection then uses protocols such as:

```text
HTTPS
```

---

# 🖥️ DNS Client

Your computer acts as a:

> **DNS Client**

Applications ask the operating system to resolve names.

Example:

```text
Browser:
"Where is www.example.com?"
```

The computer sends a DNS query toward its configured DNS resolver.

---

# 🔍 Finding Your DNS Server

On Windows:

```text
ipconfig /all
```

Look for:

```text
DNS Servers
```

You may see addresses belonging to:

- Your company
- Your router
- Your ISP
- A public DNS provider
- A VPN
- Another managed service

---

# ⚡ PowerShell

Use:

```text
Get-DnsClientServerAddress
```

This displays DNS server configuration for Windows network interfaces.

---

# 🏠 Simple DNS Resolution

Suppose PC-01 wants:

```text
server.training.local
```

and its DNS server is:

```text
192.168.10.10
```

Conceptually:

```text
PC-01
  │
  │ "What address belongs to
  │ server.training.local?"
  ▼
DNS-01
  │
  │ "192.168.20.10"
  ▼
PC-01
```

PC-01 can then communicate with:

```text
192.168.20.10
```

assuming routing and other network requirements are working.

---

# 🏗️ DNS Is Distributed

The public DNS system is not one giant server containing every name on the Internet.

DNS is:

> **Hierarchical and distributed**

A simplified hierarchy looks like:

```text
                    .
                  Root
                    │
             ┌──────┼──────┐
            com    org     net
             │
          example
             │
            www
```

---

# 🌳 DNS Root

At the top is the:

```text
.
```

DNS root.

You usually don't type the final dot, but a fully qualified domain name can conceptually end at the DNS root.

Example:

```text
www.example.com.
```

---

# 🌎 Root DNS Servers

Root DNS servers help resolvers locate the DNS servers responsible for:

> **Top-Level Domains**

Examples:

```text
.com
.org
.net
.edu
.gov
```

The root server normally doesn't need to provide the final website address.

Instead, it can direct the resolver toward the next part of the DNS hierarchy.

---

# 🏷️ Top-Level Domain — TLD

In:

```text
www.example.com
```

the:

```text
.com
```

portion is the:

> **Top-Level Domain**

Other examples include:

```text
.org
.net
.edu
.gov
```

and country-code TLDs such as:

```text
.uk
.ca
.jp
```

---

# 🏢 Domain

In:

```text
www.example.com
```

the registered domain is commonly thought of as:

```text
example.com
```

The:

```text
www
```

portion identifies a host/service name beneath that domain.

---

# 📛 Fully Qualified Domain Name

FQDN stands for:

> **Fully Qualified Domain Name**

Example:

```text
server01.example.com
```

It identifies a specific name within the DNS hierarchy.

---

# 🗄️ Authoritative DNS Server

An:

> **Authoritative DNS Server**

holds authoritative DNS information for a DNS zone.

If the server is authoritative for:

```text
example.com
```

it may contain records such as:

```text
www.example.com
mail.example.com
vpn.example.com
```

---

# 🔄 Recursive DNS Resolver

Most client devices do not manually contact root, TLD, and authoritative servers themselves.

Instead, they usually ask a:

> **Recursive DNS Resolver**

The resolver does the work required to obtain the answer.

Conceptually:

```text
CLIENT
   │
   │ www.example.com?
   ▼
RECURSIVE RESOLVER
   │
   ├── Root
   │
   ├── TLD
   │
   └── Authoritative Server
   │
   ▼
ANSWER
   │
   ▼
CLIENT
```

Caching may allow the resolver to skip some of these steps.

---

# 🔎 Recursive vs. Iterative Queries

At a high level:

## Recursive

The client asks:

> **Give me the answer.**

The recursive resolver performs the necessary work.

## Iterative

A DNS server may respond:

> **I don't have the final answer, but ask this server next.**

For beginner troubleshooting, the important idea is:

> Your computer usually relies on a recursive resolver rather than walking the entire public DNS hierarchy itself.

---

# 🗂️ DNS Zones

A:

> **DNS Zone**

is an administratively managed portion of DNS namespace.

Example:

```text
training.local
```

could contain:

```text
www.training.local
server.training.local
mail.training.local
```

A zone contains DNS records describing those names.

---

# 📄 DNS Records

DNS information is stored using different:

> **Record Types**

Different record types serve different purposes.

For Network+, you should recognize several important ones.

---

# 🅰️ A Record

An:

> **A Record**

maps a name to an:

> **IPv4 address**

Example:

```text
server.training.local
        ↓
192.168.20.10
```

Think:

```text
A
=
IPv4 Address
```

---

# 🅰️🅰️🅰️🅰️ AAAA Record

An:

> **AAAA Record**

maps a name to an:

> **IPv6 address**

Example:

```text
server.example.com
        ↓
2001:db8:20::10
```

Memory aid:

```text
A
IPv4

AAAA
IPv6
```

---

# 🔗 CNAME Record

CNAME means:

> **Canonical Name**

A CNAME creates an alias from one DNS name to another DNS name.

Example:

```text
portal.example.com
        ↓
www.example.com
```

Think:

> **Alias → Canonical Name**

---

# ✉️ MX Record

MX means:

> **Mail Exchange**

MX records identify mail servers responsible for receiving email for a domain.

Example conceptually:

```text
example.com
     ↓
MX
     ↓
mail.example.com
```

---

# 🔙 PTR Record

A:

> **PTR Record**

is commonly used for reverse DNS lookups.

Normal forward lookup:

```text
server.example.com
        ↓
192.168.10.20
```

Reverse lookup:

```text
192.168.10.20
        ↓
server.example.com
```

PTR records support the reverse direction.

---

# 🗺️ NS Record

NS means:

> **Name Server**

NS records identify authoritative DNS servers for a domain or zone.

Conceptually:

```text
example.com
        ↓
NS
        ↓
DNS server responsible for the zone
```

---

# 📝 TXT Record

TXT records store:

> **Text information associated with a DNS name**

TXT records are used for many purposes.

Common modern uses include information related to:

- Domain verification
- Email security
- Service configuration

Examples of technologies that may use TXT records include:

```text
SPF
DKIM-related information
DMARC
```

You don't need to master those technologies in this lesson.

---

# 📋 DNS Record Quick Reference

| Record | Purpose |
|---|---|
| A | Name → IPv4 |
| AAAA | Name → IPv6 |
| CNAME | Alias → another name |
| MX | Mail server |
| PTR | Reverse lookup |
| NS | Authoritative name server |
| TXT | Text / verification / policy information |

---

# 🔄 Forward Lookup

A forward lookup typically asks:

> **What IP address belongs to this name?**

Example:

```text
www.example.com
        ↓
93.x.x.x
```

Common records:

```text
A
AAAA
```

---

# 🔙 Reverse Lookup

A reverse lookup asks:

> **What DNS name is associated with this IP address?**

This commonly involves:

```text
PTR
```

records.

---

# ⏱️ DNS TTL

TTL stands for:

> **Time To Live**

DNS records can be cached for a period of time.

The TTL helps determine:

> **How long a DNS answer may be cached before it should be refreshed.**

---

# 🧠 Why Cache DNS?

Without caching:

```text
Every Query
   ↓
Potentially Repeats DNS Resolution Work
```

With caching:

```text
First Query
   ↓
DNS Lookup
   ↓
Cache Answer
   ↓
Later Query
   ↓
Use Cached Answer
```

Benefits can include:

- Faster responses
- Reduced DNS traffic
- Reduced load on DNS infrastructure

---

# ⚠️ Caching Can Also Confuse Troubleshooting

Suppose a DNS record changes:

```text
OLD:
192.168.10.20

NEW:
192.168.10.30
```

Some clients may temporarily continue using:

```text
192.168.10.20
```

because the old answer remains cached.

This can lead to:

> "It works on one computer but not another."

---

# 🖥️ Windows DNS Cache

Display the Windows DNS resolver cache:

```text
ipconfig /displaydns
```

---

# 🧹 Flush the Windows DNS Cache

Use:

```text
ipconfig /flushdns
```

This clears the Windows DNS client resolver cache.

---

# ⚠️ Important

Flushing the client cache does not magically fix every DNS problem.

It will not fix:

- Wrong DNS records
- DNS server outages
- Routing problems
- Firewall problems
- Incorrect DHCP DNS options
- Application-specific DNS caching
- Upstream cached information

Use it when the evidence suggests cached client information may be involved.

---

# 📡 DNS Ports

Traditional DNS primarily uses:

```text
UDP 53
```

but DNS also uses:

```text
TCP 53
```

---

# 🧠 Why Both UDP and TCP?

A simplified rule is:

```text
Many Normal DNS Queries
→ UDP 53
```

while TCP 53 is also used when required, including cases involving:

- Certain larger responses
- Zone transfers
- Situations where DNS falls back to TCP

Modern DNS behavior also includes technologies such as encrypted DNS, so not every DNS lookup on a modern device will necessarily appear as plain UDP/TCP 53 traffic.

---

# ⭐ Network+ Memory Tip

Remember:

```text
DNS
=
53

UDP and TCP
```

Do not memorize:

> **DNS is UDP only**

because that is incorrect.

---

# 🔐 Encrypted DNS

Modern systems may use encrypted DNS technologies such as:

- DNS over HTTPS — DoH
- DNS over TLS — DoT

These protect DNS queries differently than traditional plaintext DNS.

This can affect troubleshooting.

For example:

> You may open Wireshark and not see the traditional UDP 53 query you expected.

---

# 🖥️ `nslookup`

One of the most useful DNS troubleshooting tools is:

```text
nslookup
```

Example:

```text
nslookup example.com
```

You may see:

- DNS server used
- DNS server address
- Resolved IPv4/IPv6 addresses

---

# 🔍 Query a Specific Record

Depending on your `nslookup` environment, you can query particular record types.

For example:

```text
nslookup -type=mx example.com
```

or:

```text
nslookup -type=ns example.com
```

---

# 🎯 Query a Specific DNS Server

You can also test against a particular resolver:

```text
nslookup example.com 8.8.8.8
```

This can help compare:

```text
Configured DNS Server
vs.
Another DNS Server
```

Use external resolvers only where your network policy permits them.

---

# ⚡ PowerShell — `Resolve-DnsName`

Windows PowerShell provides:

```text
Resolve-DnsName example.com
```

This can display records returned during resolution.

---

# 🔎 Query A Records

```text
Resolve-DnsName example.com -Type A
```

---

# 🌐 Query AAAA Records

```text
Resolve-DnsName example.com -Type AAAA
```

---

# ✉️ Query MX Records

```text
Resolve-DnsName example.com -Type MX
```

---

# 🗺️ Query NS Records

```text
Resolve-DnsName example.com -Type NS
```

---

# 📝 Query TXT Records

```text
Resolve-DnsName example.com -Type TXT
```

---

# 🔙 Reverse Lookup

Try:

```text
nslookup 8.8.8.8
```

or PowerShell:

```text
Resolve-DnsName 8.8.8.8
```

If reverse DNS is configured, you may receive a PTR-related answer.

Not every IP address necessarily has useful reverse DNS configured.

---

# 🔬 DNS in Wireshark

Traditional DNS traffic can be filtered with:

```text
dns
```

You may observe:

```text
Query
```

followed by:

```text
Response
```

---

# 📋 Useful Wireshark DNS Filters

```text
dns
```

```text
udp.port == 53
```

```text
tcp.port == 53
```

For many beginner captures:

```text
dns
```

is the easiest place to start.

---

# 🧠 DNS Query Example

Suppose you run:

```text
nslookup example.com
```

Conceptually:

```text
CLIENT
192.168.10.25
      │
      │ DNS Query
      ▼
DNS SERVER
192.168.10.5
      │
      │ DNS Response
      ▼
CLIENT
```

The answer may contain:

```text
A
AAAA
CNAME
```

or other records depending on the queried name.

---

# 🌐 DNS Then HTTPS

When visiting:

```text
www.example.com
```

you may see:

```text
1. DNS Query
        ↓
2. DNS Response
        ↓
3. Client learns IP
        ↓
4. Transport connection begins
        ↓
5. HTTPS communication
```

DNS is often one of the first pieces of application communication.

---

# 🚨 DNS Failure Pattern

One of the most useful troubleshooting tests is:

```text
ping 8.8.8.8
```

followed by:

```text
nslookup example.com
```

If IP connectivity works but name resolution fails:

> **DNS becomes a strong suspect.**

---

# ⚠️ But Be Careful

A failed `ping` to a hostname does not automatically prove DNS is broken.

There are multiple stages:

```text
Resolve Name
      ↓
Obtain IP
      ↓
Send ICMP
      ↓
Destination Responds?
```

A host can resolve correctly but refuse to respond to ICMP.

Use:

```text
nslookup
```

or:

```text
Resolve-DnsName
```

when specifically testing DNS.

---

# 🛠️ Troubleshooting Scenario 1 — IP Works, Name Fails

User reports:

> "The website won't load."

Test:

```text
nslookup server.example.com
```

fails.

But direct IP communication works.

Likely area:

> **DNS**

Investigate:

- DNS server configuration
- DNS server availability
- DNS records
- Routing to DNS server
- Firewall rules
- DHCP DNS options

---

# 🛠️ Scenario 2 — Wrong DNS Server from DHCP

Client has:

```text
IP:
192.168.10.125

Gateway:
192.168.10.1

DNS:
192.168.10.99
```

Actual DNS server:

```text
192.168.10.10
```

Possible result:

```text
IP Connectivity
✅

Name Resolution
❌
```

The root cause may actually be:

> **Incorrect DHCP configuration**

even though the symptom appears to be DNS.

---

# 🛠️ Scenario 3 — Wrong DNS Record

DNS contains:

```text
server.training.local
        ↓
192.168.20.99
```

Actual server:

```text
192.168.20.10
```

DNS itself may be responding perfectly.

The problem is:

> **The DNS data is wrong.**

This distinction matters.

---

# 🛠️ Scenario 4 — DNS Server Unreachable

Client:

```text
192.168.10.25
```

DNS server:

```text
192.168.20.10
```

If routing between those networks fails, DNS will fail even though:

> **The DNS service itself may be healthy.**

Always remember the dependency chain.

---

# 🔗 DNS Dependency Chain

```text
Physical Connectivity
        ↓
Layer 2
        ↓
IPv4 / IPv6 Configuration
        ↓
Default Gateway
        ↓
Routing
        ↓
Reach DNS Server
        ↓
DNS Service
        ↓
Correct DNS Record
        ↓
Application
```

---

# 🛠️ Scenario 5 — Stale Cache

DNS record changed from:

```text
192.168.20.10
```

to:

```text
192.168.20.20
```

One computer continues using the old answer.

Check:

```text
ipconfig /displaydns
```

If appropriate:

```text
ipconfig /flushdns
```

Then query again.

---

# 🛠️ Scenario 6 — One Name Fails

Suppose:

```text
server1.training.local
```

works.

But:

```text
server2.training.local
```

fails.

That is very different from:

> **No DNS names work.**

If most names work, investigate:

- Missing record
- Incorrect record
- Wrong record type
- Typo
- Zone-specific problem

Troubleshoot by scope.

---

# 🛠️ Scenario 7 — All Users Fail

If everyone suddenly cannot resolve any internal names:

Investigate shared dependencies such as:

- DNS server
- DNS service
- Network path
- Firewall
- DNS infrastructure
- DHCP-provided DNS settings

---

# 🧭 DNS Troubleshooting Workflow

Use:

```text
Does Client Have Valid IP?
        ↓
Correct Gateway?
        ↓
Which DNS Server Is Configured?
        ↓
Can Client Reach DNS Server?
        ↓
Does nslookup Respond?
        ↓
Does Another Name Resolve?
        ↓
Does Direct IP Work?
        ↓
Does Correct Record Exist?
        ↓
Could Cache Be Involved?
        ↓
Is Problem One Client or Many?
```

---

# 📋 Useful Windows Commands

| Command | Purpose |
|---|---|
| `ipconfig /all` | View configured DNS servers |
| `ipconfig /displaydns` | View DNS client cache |
| `ipconfig /flushdns` | Clear DNS client cache |
| `nslookup` | Query DNS |
| `Get-DnsClientServerAddress` | View DNS server configuration |
| `Resolve-DnsName` | PowerShell DNS query |
| `ping` | Supporting reachability test |
| `tracert` | Investigate path to remote DNS server |
| `Test-NetConnection` | Additional connectivity testing |

---

# 📋 DNS Quick Reference

| Concept | Meaning |
|---|---|
| DNS | Domain Name System |
| Resolver | Performs DNS resolution |
| Authoritative Server | Holds authoritative zone information |
| Root | Top of DNS hierarchy |
| TLD | Top-Level Domain |
| Zone | Managed portion of DNS namespace |
| A | Name → IPv4 |
| AAAA | Name → IPv6 |
| CNAME | Alias |
| MX | Mail server |
| PTR | Reverse lookup |
| NS | Name server |
| TXT | Text/policy/verification information |
| TTL | Cache lifetime |
| UDP 53 | Common DNS queries |
| TCP 53 | DNS when TCP is required |

---

# 🧠 Knowledge Check

### 1.

What does DNS stand for?

### 2.

What is the purpose of an A record?

### 3.

What is the purpose of an AAAA record?

### 4.

Which record creates an alias?

### 5.

Which record identifies a mail server?

### 6.

Which record is commonly associated with reverse DNS?

### 7.

Which port does DNS use?

### 8.

Does DNS use UDP, TCP, or both?

### 9.

What does TTL control?

### 10.

Which Windows command is commonly used to query DNS?

---

# ✅ Answers

1. **Domain Name System**
2. **Maps a name to an IPv4 address**
3. **Maps a name to an IPv6 address**
4. **CNAME**
5. **MX**
6. **PTR**
7. **53**
8. **Both UDP and TCP**
9. **How long DNS information may be cached**
10. **`nslookup`**

---

# 🎓 Network+ Challenge 1

A user can reach:

```text
192.168.20.10
```

but cannot reach:

```text
server.training.local
```

What service should you investigate?

> **DNS**

---

# 🎓 Network+ Challenge 2

Which DNS record maps:

```text
server.example.com
```

to:

```text
192.168.10.25
```

> **A**

---

# 🎓 Network+ Challenge 3

Which record is used for IPv6?

> **AAAA**

---

# 🎓 Network+ Challenge 4

Which record would you investigate when troubleshooting where email for a domain should be delivered?

> **MX**

---

# 🎓 Network+ Challenge 5

Which record is commonly used for reverse DNS?

> **PTR**

---

# 🎓 Network+ Challenge 6

A DNS record was corrected, but one workstation continues resolving the old address.

What should you investigate?

> **DNS caching / TTL**

---

# 🎓 Network+ Challenge 7

A client has the wrong DNS server because DHCP supplied an incorrect address.

Is the root cause necessarily the DNS server?

> **No. The root cause may be the DHCP scope configuration.**

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- DNS translates useful names into information such as IP addresses.
- DNS is hierarchical and distributed.
- Clients usually query recursive resolvers.
- Authoritative servers contain authoritative zone information.
- Root and TLD servers help navigate public DNS hierarchy.
- A records map names to IPv4.
- AAAA records map names to IPv6.
- CNAME creates aliases.
- MX identifies mail exchangers.
- PTR supports reverse DNS.
- NS identifies name servers.
- TXT stores text-based information.
- DNS uses both UDP and TCP port 53.
- DNS answers can be cached.
- TTL controls caching lifetime.
- `nslookup` and `Resolve-DnsName` are important troubleshooting tools.
- `ipconfig /displaydns` displays the Windows DNS cache.
- `ipconfig /flushdns` clears the Windows DNS client cache.
- IP working while names fail is a strong DNS troubleshooting clue.
- DNS depends on lower network layers working first.

---

# 🧪 Next Step — Lab 15

Lab 15 will use:

```text
Windows
+
PowerShell
+
Wireshark
+
Packet Tracer
```

You'll:

- Identify your configured DNS server
- Perform A, AAAA, MX, NS, and reverse lookups
- Inspect the Windows DNS cache
- Capture DNS queries
- Observe DNS responses
- Compare DNS with HTTPS traffic
- Build an internal DNS server
- Create DNS records
- Break DNS without breaking IP connectivity
- Troubleshoot wrong DNS records
- Troubleshoot wrong DNS server configuration

➡️ **[Lab 15 — DNS](../labs/lab-15-dns.md)**

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
        ↓
🟡 NEXT: Lab 15

⬜ Lesson 16 — NAT & Address Translation
⬜ Lab 16

        ↓

🏗️ Project 03
Build a Routed Small-Business Network
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**