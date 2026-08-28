# Lab 19 — NAT and PAT Fundamentals

## Lab Objective

Build a private/public training topology, observe NAT/PAT translations, and troubleshoot common translation failures.

---

# Part 1 — Review Address Types

Classify:

```text
192.168.190.10  __________________
10.10.10.10     __________________
203.0.113.10    __________________
198.51.100.20   __________________
```

For this lab, the last two are documentation addresses representing public-side networks.

---

# Part 2 — Build the Topology

Packet Tracer:

```text
PC0 ──┐
PC1 ──┼── Switch ── Router ── Outside Server
PC2 ──┘
```

Inside network:

```text
192.168.190.0/24
Gateway: 192.168.190.1
```

Outside documentation network:

```text
203.0.113.0/24
```

Configure addresses appropriate to your router interfaces.

---

# Part 3 — Verify Routing Before NAT

Confirm local connectivity first.

Ask:

```text
Can inside hosts reach gateway?
Are router interfaces up?
Is outside routing correct?
```

Do not troubleshoot NAT before verifying the underlying network.

---

# Part 4 — Configure PAT

Using the NAT/PAT capabilities available in your Packet Tracer router, configure inside hosts to translate through the outside interface.

Exact Cisco commands can vary by topology and device.

Document the configuration you used.

---

# Part 5 — Generate Traffic

From multiple inside PCs, communicate with the outside server.

Inspect NAT translations using the router commands supported by your device, commonly including commands similar to:

```text
show ip nat translations
show ip nat statistics
```

Record what changes.

---

# Part 6 — Explain PAT

For two internal clients, document conceptually:

```text
Inside client 1: ______________________
Inside client 2: ______________________
Shared translated address: ____________
How are conversations distinguished? __
```

---

# Part 7 — Break NAT

Remove or misconfigure one NAT component in the isolated lab.

Possible faults:

```text
Wrong inside network match
Wrong inside/outside designation
Missing translation rule
Incorrect route
```

Troubleshoot systematically.

---

# Part 8 — NAT vs. DNS

Scenario:

```text
External IP works
External hostname fails
```

Is NAT automatically the root cause?

```text
Yes / No
```

What should you test?

```text
____________________________________
```

---

# Part 9 — Port Forwarding Design

Do not expose a real service.

On paper only, document what a rule would conceptually do:

```text
Public training address: 203.0.113.10
Public port: 443
Internal server: 192.168.190.20
Internal port: 443
```

What security questions should be answered before publishing a service?

---

# Part 10 — Troubleshooting Flow

Create:

```text
Client IP
   ↓
Gateway
   ↓
Routing
   ↓
NAT/PAT configuration
   ↓
Firewall/policy
   ↓
Upstream
   ↓
DNS/application
```

---

# Knowledge Check

1. What does PAT add to address translation?
2. Why should routing be verified before NAT?
3. What can a NAT translation table show?
4. Is port forwarding automatically safe?
5. Does IPv6 require NAT for address conservation?

---

# Challenge

Build at least three private clients that share one translated address using PAT.

Prove all three can reach the outside training server.

Then create two faults:

```text
One addressing/routing fault
One NAT configuration fault
```

Determine which layer/component is responsible before repairing each.

Save:

```text
lab-19-nat-pat-challenge.pkt
```

---

# Lab Completion Checklist

- [ ] Classified private/documentation addresses
- [ ] Built inside/outside topology
- [ ] Verified routing baseline
- [ ] Configured PAT
- [ ] Generated translated traffic
- [ ] Inspected translations
- [ ] Explained PAT
- [ ] Diagnosed broken NAT
- [ ] Distinguished NAT from DNS
- [ ] Reviewed port forwarding safely
- [ ] Built troubleshooting flow
- [ ] Completed knowledge check
- [ ] Completed challenge

---

# Lab Complete

You have completed **Lab 19 — NAT and PAT Fundamentals** and **Section 4 — Transport & Network Services**.

You now have hands-on experience with:

```text
TCP
UDP
Ports
TCP handshakes
Service testing
Wireshark filtering
DNS
DNS records
DNS troubleshooting
DHCP
DORA
DHCP scopes and leases
DHCP relay concepts
NAT
PAT
Translation troubleshooting
```

Now apply those skills in Project 04.

---

# 🛠️ Project 04 — Deploy Core Network Services

➡️ **[Project 04 — Deploy Core Network Services](../projects/project-04-deploy-core-network-services.md)**

You will build a small-business network that provides addressing, DNS, application services, and Internet-style connectivity through NAT/PAT.

➡️ **[Begin Project 04 — Deploy Core Network Services](../projects/project-04-deploy-core-network-services.md)**
