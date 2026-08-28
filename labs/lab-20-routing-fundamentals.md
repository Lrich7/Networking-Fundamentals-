# Lab 20 — Routing Fundamentals

## Lab Objective

Build multiple routed networks, inspect routing tables, configure static/default routes, and troubleshoot routing failures.

---

# Part 1 — Inspect Windows Routes

Run:

```powershell
Get-NetRoute -AddressFamily IPv4
```

Then:

```text
route print
```

Locate:

```text
Local network route
Default route
Loopback-related routes
```

Do not publish internal company routes.

---

# Part 2 — Build Two LANs

Packet Tracer:

```text
PC0 ─ Switch0 ─ Router ─ Switch1 ─ PC1
```

Use:

```text
LAN A: 192.168.200.0/24
LAN B: 192.168.201.0/24
```

Router:

```text
LAN A: 192.168.200.1
LAN B: 192.168.201.1
```

Configure valid host addresses and gateways.

---

# Part 3 — Verify Routing

Test:

```text
PC0 → LAN A gateway
PC1 → LAN B gateway
PC0 → PC1
```

Record the results.

---

# Part 4 — Inspect Router Routes

Run:

```text
show ip route
```

Identify the directly connected routes.

Explain why no static route is required between networks directly attached to the same router.

---

# Part 5 — Add a Second Router

Build:

```text
LAN A ─ R1 ─ R2 ─ LAN B
```

Use a separate transit network between routers.

Document all three networks.

---

# Part 6 — Static Routes

Configure static routes so each router knows how to reach the remote LAN.

Verify end-to-end connectivity.

Document:

```text
R1 remote route:
R2 remote route:
```

---

# Part 7 — Break the Return Route

Remove the remote route from one router.

Test again.

Explain why one correct forward route is not enough.

---

# Part 8 — Wrong Gateway

Give one PC the wrong gateway.

Test:

```text
Local host
Local router
Remote host
```

Document the symptoms and repair the problem.

---

# Part 9 — Traceroute

Use:

```text
tracert <destination>
```

or the Packet Tracer equivalent.

Record the Layer 3 devices in the path.

---

# Knowledge Check

1. What command shows the Cisco IPv4 routing table?
2. What command shows Windows routes?
3. Why are directly connected routes created?
4. What is a next hop?
5. Why must return routing work?

---

# Challenge

Build:

```text
LAN A ─ R1 ─ R2 ─ R3 ─ LAN B
```

Use static routes to provide end-to-end connectivity.

Then remove one route and identify the failure using routing tables rather than guessing.

Save:

```text
lab-20-routing-fundamentals.pkt
```

---

# Lab Completion Checklist

- [ ] Inspected Windows routes
- [ ] Built two routed LANs
- [ ] Inspected connected routes
- [ ] Added second router
- [ ] Configured static routes
- [ ] Tested return routing
- [ ] Diagnosed wrong gateway
- [ ] Used traceroute
- [ ] Completed knowledge check
- [ ] Completed challenge

---

# Lab Complete

You have completed **Lab 20 — Routing Fundamentals**.

# Next Lesson

➡️ **[Lesson 21 — Switching Fundamentals](../lessons/lesson-21-switching-fundamentals.md)**
