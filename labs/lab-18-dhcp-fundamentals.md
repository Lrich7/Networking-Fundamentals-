# Lab 18 — DHCP Fundamentals

## Lab Objective

Inspect DHCP client information, configure a DHCP service in Packet Tracer, observe DORA, and troubleshoot common DHCP failures.

---

# Part 1 — Inspect DHCP Status

Run:

```text
ipconfig /all
```

Identify whether your active adapter uses DHCP.

Do not publish internal server addresses.

---

# Part 2 — DHCP Information

Record conceptually:

```text
DHCP enabled? __________________
Lease obtained? ________________
Lease expiration? ______________
Gateway supplied? ______________
DNS supplied? ___________________
```

---

# Part 3 — Build Packet Tracer Network

Create:

```text
PC0 ──┐
PC1 ──┼── Switch ── Router
PC2 ──┘
```

Use:

```text
192.168.180.0/24
Gateway: 192.168.180.1
```

Add a DHCP-capable server or configure DHCP on a supported router.

---

# Part 4 — Create DHCP Pool

Example:

```text
Pool start: 192.168.180.50
Gateway:    192.168.180.1
DNS:        192.168.180.10
```

Choose a suitable number of addresses.

Set clients to DHCP.

---

# Part 5 — Verify Leases

Record:

```text
PC0: __________________
PC1: __________________
PC2: __________________
```

Confirm each received:

```text
Unique IP
Correct mask
Correct gateway
Expected DNS
```

---

# Part 6 — Observe DORA

Use Simulation Mode.

Trigger a DHCP client process.

Identify:

```text
Discover
Offer
Request
Acknowledge
```

Record the order.

---

# Part 7 — Scope Failure

Disable the DHCP service or create an intentionally unusable pool in the isolated lab.

Observe client behavior.

What clue might Windows show in a similar real-world failure?

```text
____________________________________
```

Restore DHCP.

---

# Part 8 — Exhaustion Scenario

Scenario:

```text
DHCP pool has 20 addresses
All 20 are leased
New client connects
```

What happens?

What should the administrator investigate before simply expanding the scope?

---

# Part 9 — Wrong Gateway Option

Configure the DHCP pool with an incorrect gateway.

Clients still receive addresses.

Test local vs. routed communication.

Explain the symptom.

Restore the correct gateway.

---

# Part 10 — DHCP Relay Reasoning

Add or diagram a second routed subnet.

Explain why a DHCP server on another subnet may require a relay/helper function.

You do not have to configure relay if your current Packet Tracer device/version makes it impractical.

---

# Knowledge Check

1. What does the DHCP Discover do?
2. What is a DHCP lease?
3. Why are exclusions useful?
4. What happens when a scope is exhausted?
5. Why can a client receive an IP but still have a bad network configuration?

---

# Challenge

Create two DHCP pools for two routed LANs.

If supported, configure relay so a centralized DHCP server can serve the remote LAN.

Verify clients receive addresses from the correct subnet.

Then break one DHCP option and diagnose it.

Save:

```text
lab-18-dhcp-fundamentals.pkt
```

---

# Lab Completion Checklist

- [ ] Inspected DHCP client status
- [ ] Built DHCP lab
- [ ] Created a DHCP pool
- [ ] Verified leases
- [ ] Observed DORA
- [ ] Diagnosed DHCP service failure
- [ ] Analyzed scope exhaustion
- [ ] Diagnosed wrong gateway option
- [ ] Explained DHCP relay
- [ ] Completed knowledge check
- [ ] Completed challenge

---

# Lab Complete

You have completed **Lab 18 — DHCP Fundamentals**.

# Next Lesson

➡️ **[Lesson 19 — NAT and PAT Fundamentals](../lessons/lesson-19-nat-and-pat-fundamentals.md)**
