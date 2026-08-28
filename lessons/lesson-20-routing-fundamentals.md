# Lesson 20 — Routing Fundamentals

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain the purpose of routing.
- Distinguish local and remote networks.
- Explain how a host uses its default gateway.
- Read a basic routing table.
- Explain directly connected, static, and default routes.
- Describe longest-prefix matching at a beginner level.
- Use Windows and Cisco tools to inspect routes.
- Troubleshoot common routing failures.

---

# What Is Routing?

Routing is the process of moving IP packets between different networks.

```text
LAN A
192.168.20.0/24
      |
   Router
      |
LAN B
192.168.21.0/24
```

Devices on the same subnet can communicate locally.

Devices on different subnets normally require a router or Layer 3 device.

---

# The Default Gateway

A host compares the destination IP with its own network.

If the destination is remote:

```text
Host
  ↓
Default Gateway
  ↓
Router
  ↓
Remote Network
```

The gateway must normally be reachable on the host's local subnet.

---

# Routing Tables

Routers use routing tables to decide where packets should go.

A route contains information such as:

```text
Destination network
Prefix / mask
Next hop
Outgoing interface
Route source
Metric
```

---

# Directly Connected Routes

When a router interface is configured and active, the router knows about that attached network.

Example:

```text
G0/0 → 192.168.20.1/24
```

The router can identify:

```text
192.168.20.0/24
```

as directly connected.

---

# Static Routes

A static route is manually configured.

Conceptually:

```text
To reach 10.20.0.0/16
send traffic to 192.168.1.2
```

Static routes are predictable but must be maintained by an administrator.

---

# Default Route

A default route is used when no more-specific route matches.

IPv4:

```text
0.0.0.0/0
```

Conceptually:

```text
Unknown destination
       ↓
Default route
       ↓
Upstream router
```

---

# Longest Prefix Match

If multiple routes match a destination, routers prefer the most specific matching prefix.

Example:

```text
10.0.0.0/8
10.10.0.0/16
10.10.20.0/24
```

For destination:

```text
10.10.20.50
```

the `/24` is the most specific match.

---

# Windows Routing Table

Command Prompt:

```text
route print
```

PowerShell:

```powershell
Get-NetRoute
```

IPv4 only:

```powershell
Get-NetRoute -AddressFamily IPv4
```

---

# Cisco Routing Table

Common command:

```text
show ip route
```

You may see codes representing route sources.

For now, focus on recognizing:

```text
Connected
Local
Static
Default
```

---

# Routing Troubleshooting

Use a structured process:

```text
Host IP correct?
      ↓
Mask correct?
      ↓
Gateway correct?
      ↓
Gateway reachable?
      ↓
Router interface up?
      ↓
Route to destination?
      ↓
Return route exists?
      ↓
Policy/firewall?
```

A route must work in both directions for normal two-way communication.

---

# Key Terms

```text
Router
Route
Routing Table
Next Hop
Default Gateway
Static Route
Default Route
Directly Connected
Longest Prefix Match
Return Route
```

---

# Knowledge Check

1. What is the purpose of a router?
2. When does a host use its default gateway?
3. What does `0.0.0.0/0` represent?
4. What is a static route?
5. What does longest-prefix match mean?
6. Why is a return route important?

---

# Hands-On Lab

➡️ **[Lab 20 — Routing Fundamentals](../labs/lab-20-routing-fundamentals.md)**
