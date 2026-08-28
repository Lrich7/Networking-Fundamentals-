# Lab 33 — Windows Networking Commands

## Lab Objective

Practice windows networking commands using a repeatable, evidence-based IT troubleshooting workflow.

---

# Safety and Privacy

- Work only on systems and networks you own or are authorized to administer.
- Use Packet Tracer or isolated training environments for intentional faults.
- Prefer read-only inspection on real systems.
- Do not publish company IPs, routes, DNS records, packet captures, credentials, or configurations.
- Never disable security controls simply to make troubleshooting easier.

---

# Part 1 — Establish a Baseline

Before introducing a fault, verify and document:

```text
Physical/link state
IP configuration
Default gateway
DNS
Expected routes
Expected VLAN
Required service/port
Known-good test result
```

---

# Part 2 — Main Exercise

On a Windows training machine, practice `ipconfig /all`, `ping`, `tracert`, `nslookup`, `arp -a`, and `netstat -ano`. Record what question each command answers. Use public/safe destinations and do not publish internal company details.

---

# Part 3 — Determine Scope

For each issue, classify the scope:

```text
Single endpoint
Multiple endpoints
One VLAN/subnet
One switch/router
One service
Multiple networks
Site-wide
```

Explain why the evidence supports your answer.

---

# Part 4 — Layer Isolation

Use the OSI/TCP-IP models to identify the likely area:

```text
Layer 1 → link/cable/interface
Layer 2 → MAC/VLAN/trunk/STP
Layer 3 → IP/mask/gateway/route
Layer 4 → TCP/UDP/port
Layer 7 → DNS/application/service
```

---

# Part 5 — Ticket Record

For at least two scenarios complete:

```text
Ticket:
Reported issue:
Affected scope:
Baseline:
Evidence:
Theory:
Test:
Root cause:
Correction:
Verification:
Follow-up:
```

---

# Part 6 — Verification

Do not stop after one successful ping.

Verify relevant functions such as:

```text
Local connectivity
Gateway
Remote network
DNS resolution
Required TCP/UDP service
Application
Other affected users
```

---

# Knowledge Check

1. What evidence was most useful?
2. Which layer contained the root cause?
3. What test eliminated the most incorrect theories?
4. How did scope help?
5. What did you verify after repair?

---

# Challenge

Create three additional faults in the isolated lab.

For each, do **not** write down the answer beside the fault. Return later and troubleshoot from symptoms and evidence as though it were a real ticket.

---

# Lab Completion Checklist

- [ ] Established baseline
- [ ] Completed main exercise
- [ ] Determined scope
- [ ] Used layer isolation
- [ ] Documented two tickets
- [ ] Verified full functionality
- [ ] Completed knowledge check
- [ ] Completed challenge

---

# Lab Complete

You have completed **Lab 33 — Windows Networking Commands**.

# Next Lesson

➡️ **[Lesson 34 — PowerShell Networking Tools](../lessons/lesson-34-powershell-networking-tools.md)**

