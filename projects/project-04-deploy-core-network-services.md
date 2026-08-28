# Project 04 — Deploy Core Network Services

## Project Overview

You have completed Section 4 — **Transport & Network Services**.

Your task is to deploy and troubleshoot the core services a small business depends on:

```text
TCP/IP application connectivity
DNS
DHCP
NAT/PAT
```

Unlike the labs, this project gives you requirements rather than exact step-by-step configuration.

---

# Scenario

A small company has approximately 40 users.

The office needs:

```text
Automatic client addressing
Internal DNS
An internal web server
A routed Internet-style connection
PAT for client outbound connectivity
Reliable troubleshooting documentation
```

Use only fictional/training addresses and names.

---

# Requirements

Build a representative environment containing at least:

```text
4 client PCs
1 switch
1 router
1 DHCP service
1 DNS service
1 internal web server
1 outside test server/network
```

Services can share a Packet Tracer server if appropriate.

---

# Part 1 — Address Plan

Use:

```text
Internal network: 192.168.200.0/24
Gateway:          192.168.200.1
```

Reserve sensible static addresses for infrastructure.

Create a DHCP range for clients.

Document:

```text
Gateway:
DNS server:
Web server:
DHCP range:
Excluded/reserved range:
Outside documentation network:
```

Use an outside documentation range such as:

```text
203.0.113.0/24
```

---

# Part 2 — Build the Topology

Your design should resemble:

```text
Clients
   │
 Switch
   │
   ├──── DNS/DHCP/Web Services
   │
 Router / NAT
   │
Outside Training Network
   │
Outside Server
```

---

# Part 3 — Configure DHCP

Clients must automatically receive:

```text
IPv4 address
Subnet mask
Default gateway
DNS server
```

Verify at least four unique leases.

---

# Part 4 — Configure DNS

Create a fictional internal record such as:

```text
intranet.training.local
```

pointing to your internal web server.

Verify clients can resolve the name.

---

# Part 5 — Configure Web Service

Enable an HTTP service on the internal training server if supported.

Test:

```text
By IP
By DNS name
```

Explain why both tests are useful.

---

# Part 6 — Validate Ports

Document the relevant ports/protocols used in your design.

Include at least:

```text
DNS
DHCP
HTTP
HTTPS concept
```

For each, record:

```text
Port
TCP/UDP
Purpose
```

---

# Part 7 — Configure PAT

Configure outbound translation so multiple internal clients can reach the outside training network using the router's translated/public-side address.

Verify multiple clients create translations.

---

# Part 8 — Inspect the Translation Table

Generate traffic from several clients.

Inspect NAT translations.

Explain how PAT keeps the conversations separate.

---

# Part 9 — Observe Traffic

Use Packet Tracer Simulation Mode and/or a safe Wireshark training capture to observe at least two of:

```text
DHCP
DNS
TCP handshake
HTTP
NAT/PAT-related flow
```

Document what happens at Layers 3 and 4.

---

# Part 10 — Failure Ticket 1: DHCP

Create one DHCP fault.

Examples:

```text
DHCP disabled
Bad pool
Wrong gateway option
Scope exhausted
```

Document:

```text
Symptom
Scope
Evidence
Root cause
Fix
Verification
```

---

# Part 11 — Failure Ticket 2: DNS

Create:

```text
Wrong client DNS server
```

or:

```text
Incorrect DNS record
```

Prove IP connectivity still works if appropriate, then diagnose name resolution.

---

# Part 12 — Failure Ticket 3: Application Port

Create a scenario where:

```text
Server IP reachable
Web service unavailable
```

Troubleshoot beyond ping.

Document the service/port checks you would perform.

---

# Part 13 — Failure Ticket 4: NAT/PAT

Break the NAT/PAT configuration.

Verify:

```text
Internal communication
Gateway communication
Outside communication
```

Use the results to isolate the failure.

---

# Part 14 — Failure Ticket 5: Wrong Gateway

Give one DHCP client or statically configured host the wrong gateway.

Compare:

```text
Local DNS/web access
Outside network access
```

Explain the result.

---

# Part 15 — Build a Service Troubleshooting Matrix

Create documentation similar to:

```text
Symptom:
Possible layer/service:
First test:
Second test:
Likely tools:
```

Cover:

```text
No IP address
169.254.x.x
Can ping IP but not name
Can ping server but web fails
Local works but outside fails
One port fails
All clients fail
```

---

# Part 16 — Final Network Documentation

Your final documentation should contain:

```text
Topology
Address plan
DHCP pool
DNS records
Server addresses
Default gateway
Outside training network
NAT/PAT design
Common ports
Testing results
Known troubleshooting commands
```

Another technician should be able to understand the lab without opening Packet Tracer first.

---

# Part 17 — Save the Project

Save:

```text
project-04-deploy-core-network-services.pkt
```

Recommended repository location:

```text
packet-tracer/projects/
```

Do not upload real company packet captures, internal DNS information, or public IP details.

---

# Final Validation

- [ ] Topology built
- [ ] Address plan documented
- [ ] DHCP configured
- [ ] Four or more clients receive valid leases
- [ ] DNS configured
- [ ] Internal name resolves
- [ ] Web service tested by IP
- [ ] Web service tested by name
- [ ] Common ports documented
- [ ] PAT configured
- [ ] Multiple translations verified
- [ ] Protocol traffic observed
- [ ] DHCP fault diagnosed
- [ ] DNS fault diagnosed
- [ ] Application-port fault diagnosed
- [ ] NAT/PAT fault diagnosed
- [ ] Gateway fault diagnosed
- [ ] Troubleshooting matrix completed
- [ ] Final network documentation completed
- [ ] Packet Tracer file saved

---

# Project Reflection

1. Why is ping alone insufficient for application troubleshooting?
2. How does DNS depend on working IP connectivity?
3. What information does DHCP automate?
4. Why is DORA useful to understand during troubleshooting?
5. How does PAT allow many clients to share one translated IPv4 address?
6. Which failure was easiest to isolate?
7. Which failure could most easily be mistaken for another problem?

---

# 🏆 Project Complete

You have completed **Project 04 — Deploy Core Network Services**.

You have now applied:

```text
TCP
UDP
Ports
DNS
DHCP
DORA
Service testing
Wireshark/Simulation Mode
NAT
PAT
Layered troubleshooting
Network documentation
```

---

# ➡️ Continue Training

Next:

➡️ **[Lesson 20 — Routing Fundamentals](../lessons/lesson-20-routing-fundamentals.md)**
