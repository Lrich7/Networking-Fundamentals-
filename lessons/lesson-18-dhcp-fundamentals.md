# Lesson 18 — DHCP Fundamentals

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain the purpose of DHCP.
- Describe the DHCP DORA process.
- Recognize DHCP scopes, pools, leases, exclusions, and reservations.
- Identify common DHCP-provided settings.
- Explain why DHCP relay is needed across routed networks.
- Use Windows tools to inspect and renew DHCP configuration.
- Recognize APIPA as a DHCP troubleshooting clue.
- Configure and troubleshoot DHCP in Packet Tracer.

---

# What Is DHCP?

**Dynamic Host Configuration Protocol (DHCP)** automatically provides network configuration to clients.

Typical information includes:

```text
IPv4 address
Subnet mask
Default gateway
DNS servers
Lease information
```

Without DHCP, administrators may need to manually configure every endpoint.

---

# DORA

A common way to remember initial DHCPv4 communication:

```text
Discover
Offer
Request
Acknowledge
```

or:

```text
D
O
R
A
```

---

# DHCP Ports

DHCPv4 commonly uses UDP:

```text
Server: UDP 67
Client: UDP 68
```

---

# Scope / Pool

A DHCP scope or pool defines addresses available for assignment.

Example:

```text
Network: 192.168.180.0/24
Pool:    192.168.180.50–192.168.180.200
Gateway: 192.168.180.1
DNS:     192.168.180.10
```

---

# Exclusions

Addresses can be excluded from dynamic assignment.

Examples:

```text
Router
Servers
Network appliances
Statically assigned infrastructure
```

---

# Reservations

A reservation associates a specific client identity—commonly based on MAC/client identifier—with a predictable DHCP assignment.

Reservations are useful when a device should consistently receive a particular address while still being centrally managed through DHCP.

---

# Leases

DHCP assignments are leased for a period of time.

Clients renew leases rather than treating an address as permanently owned.

---

# DHCP Across Routers

Initial DHCP discovery relies on local broadcast behavior.

Routers do not normally forward ordinary broadcasts between subnets.

To use a centralized DHCP server for another subnet, a **DHCP relay** can forward the required DHCP information.

---

# APIPA

If Windows expects DHCP but cannot obtain an IPv4 lease, it may assign:

```text
169.254.x.x
```

This is a clue, not a complete diagnosis.

Possible causes include:

```text
Disconnected client
Wrong VLAN
DHCP server unavailable
Scope exhausted
Relay misconfiguration
Firewall/path issue
Client problem
```

---

# Windows DHCP Inspection

```text
ipconfig /all
```

Look for:

```text
DHCP Enabled
DHCP Server
Lease Obtained
Lease Expires
```

Renew commands:

```text
ipconfig /release
ipconfig /renew
```

Do not release an address on a remote production system unless you understand the risk of losing connectivity.

---

# DHCP Troubleshooting Flow

```text
Client connected?
      ↓
Correct VLAN/subnet?
      ↓
DHCP enabled?
      ↓
Discover leaves client?
      ↓
Server/scope available?
      ↓
Relay configured if remote?
      ↓
Offer returns?
      ↓
Valid lease/options?
```

---

# Key Terms

```text
DHCP
DORA
Scope
Pool
Lease
Exclusion
Reservation
DHCP Relay
APIPA
UDP 67
UDP 68
```

---

# Knowledge Check

1. What does DORA stand for?
2. What information can DHCP provide?
3. What ports does DHCPv4 use?
4. What is a reservation?
5. Why might DHCP relay be required?
6. What can APIPA indicate?

---

# Hands-On Lab

➡️ **[Lab 18 — DHCP Fundamentals](../labs/lab-18-dhcp-fundamentals.md)**
