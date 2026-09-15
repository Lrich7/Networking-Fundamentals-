# 🧪 Lab 07 — IPv4 Addressing

Welcome to **Lab 07 of Networking Fundamentals**.

In Lesson 07, you learned how IPv4 addresses identify devices and networks.

Now you'll work directly with:

```text
IPv4 Addresses
Subnet Masks
Default Gateways
Private Addresses
Loopback
APIPA
Static Configuration
DHCP Configuration
```

using:

```text
Windows
+
PowerShell
+
Cisco Packet Tracer
```

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Identify your computer's IPv4 configuration
- Identify your subnet mask
- Identify your default gateway
- Identify your DNS servers
- Determine whether an address is private
- Test loopback communication
- Recognize APIPA
- Use `ipconfig`
- Use `Get-NetIPConfiguration`
- Use `Get-NetIPAddress`
- Build two IPv4 networks in Packet Tracer
- Configure static IPv4 addresses
- Configure default gateways
- Test local connectivity
- Test routed connectivity
- Troubleshoot incorrect addresses
- Troubleshoot incorrect subnet masks
- Troubleshoot incorrect gateways
- Recognize duplicate address problems

---

# 🎓 Network+ Focus

This lab reinforces:

- IPv4
- Private IPv4 addressing
- Subnet masks
- CIDR
- APIPA
- Loopback
- Default gateways
- Static addressing
- DHCP
- Network addresses
- Broadcast addresses
- IPv4 troubleshooting

---

# ⏱️ Estimated Time

**60–75 minutes**

---

# ⚠️ Important Safety Note

During the Windows portion:

> **Do not change the IPv4 configuration of a work computer or production network adapter.**

You'll inspect your real configuration, but configuration changes will be performed safely inside:

> **Cisco Packet Tracer**

---

# 🖥️ PART 1 — WINDOWS IPV4

# Step 1 — Examine Basic Configuration

Open Command Prompt.

Run:

```cmd
ipconfig
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

Record:

```text
IPv4 Address:

____________________________________

Subnet Mask:

____________________________________

Default Gateway:

____________________________________
```

---

# Step 2 — Detailed Configuration

Run:

```cmd
ipconfig /all
```

Find the same adapter.

Record:

```text
DHCP Enabled:

____________________________________

IPv4 Address:

____________________________________

Subnet Mask:

____________________________________

Default Gateway:

____________________________________

DNS Server(s):

____________________________________
```

---

# 🧠 Question

Was your IPv4 configuration most likely:

### A. Static

### B. DHCP

Answer:

```text
____________________________________
```

Look at:

```text
DHCP Enabled
```

for evidence.

---

# 🔷 Step 3 — PowerShell

Open PowerShell.

Run:

```powershell
Get-NetIPConfiguration
```

Compare the output with:

```cmd
ipconfig
```

Identify:

- Interface
- IPv4 address
- Default gateway
- DNS server

---

# Step 4 — View IP Addresses

Run:

```powershell
Get-NetIPAddress -AddressFamily IPv4
```

You may see more IPv4 addresses than expected.

Why?

Your computer may have:

- Physical interfaces
- Virtual interfaces
- VPN adapters
- Loopback-related interfaces

---

# 📝 Record Your Active Address

```text
Interface:

____________________________________

IPv4 Address:

____________________________________

Prefix Length:

____________________________________
```

---

# 🧠 Prefix Length

If you see:

```text
PrefixLength : 24
```

that corresponds to:

```text
/24
```

and normally:

```text
255.255.255.0
```

---

# 🔁 Step 5 — Test Loopback

Run:

```cmd
ping 127.0.0.1
```

Record:

```text
PASS / FAIL
```

---

# 🧠 What Did You Test?

You tested:

> **Your own local TCP/IP stack**

You did **not** prove that:

- The Internet works
- Your router works
- DNS works
- Wi-Fi works
- Another device is reachable

---

# 🚪 Step 6 — Test Your Gateway

Run:

```cmd
ping YOUR_GATEWAY
```

Example:

```cmd
ping 192.168.1.1
```

Record:

```text
PASS / FAIL
```

Note: Some gateways may be configured not to respond to ICMP. A failed ping alone does not prove the gateway is unavailable.

---

# 🌎 Step 7 — Test a Remote IPv4 Address

Run:

```cmd
ping 8.8.8.8
```

Record:

```text
PASS / FAIL
```

Again, ICMP may be filtered in some environments.

---

# 🌐 Step 8 — Test Name Resolution

Run:

```cmd
nslookup example.com
```

Record one returned address:

```text
____________________________________
```

---

# 🧠 Troubleshooting Comparison

Consider these tests:

```text
127.0.0.1
      ↓
Default Gateway
      ↓
Remote IP
      ↓
DNS Name
```

Each tests something different.

This helps you narrow down where a problem may exist.

---

# 🏠 Step 9 — Identify Your Address Type

Look at your IPv4 address.

Does it fall within:

```text
10.0.0.0/8
```

or:

```text
172.16.0.0/12
```

or:

```text
192.168.0.0/16
```

If yes, your address is:

> **RFC 1918 Private IPv4**

Record:

```text
My IPv4 address is:

PRIVATE / OTHER
```

---

# ⚠️ Step 10 — APIPA Recognition

Do **not** intentionally break your work network to create APIPA.

Instead, examine this example:

```text
IPv4 Address:
169.254.77.25

Subnet Mask:
255.255.0.0

Default Gateway:
None
```

What does this suggest?

```text
____________________________________

____________________________________
```

Expected answer:

> The device has an IPv4 link-local/APIPA address and may have failed to obtain its expected DHCP configuration.

---

# 🌐 PART 2 — PACKET TRACER

# Step 11 — Build Network A

Open Cisco Packet Tracer.

Add:

```text
PC-A
PC-B
SW-A
```

Connect:

```text
PC-A ──┐
       │
      SW-A
       │
PC-B ──┘
```

---

# Step 12 — Configure Network A

Use:

```text
192.168.10.0/24
```

Configure:

| Device | IPv4 | Mask |
|---|---|---|
| PC-A | 192.168.10.10 | 255.255.255.0 |
| PC-B | 192.168.10.20 | 255.255.255.0 |

Do not configure a gateway yet.

---

# Step 13 — Test Local Communication

From PC-A:

```cmd
ping 192.168.10.20
```

Record:

```text
PASS / FAIL
```

---

# 🧠 Why Does This Work Without a Gateway?

```text
____________________________________________________

____________________________________________________
```

Expected concept:

> Both hosts belong to the same local IPv4 subnet.

---

# 🗺️ Step 14 — Identify the /24 Information

For:

```text
192.168.10.0/24
```

complete:

```text
Network Address:

____________________________________

First Usable Host:

____________________________________

Last Usable Host:

____________________________________

Broadcast Address:

____________________________________
```

Answers:

```text
Network:
192.168.10.0

First:
192.168.10.1

Last:
192.168.10.254

Broadcast:
192.168.10.255
```

---

# 🚦 PART 3 — ADD ANOTHER NETWORK

# Step 15 — Add Router and Network B

Add:

```text
R-01
SW-B
PC-C
```

Build:

```text
PC-A ──┐
       │
      SW-A
       │
PC-B ──┘
       │
      R-01
       │
      SW-B
       │
      PC-C
```

---

# Step 16 — Configure R-01

Configure the interface facing Network A as:

```text
192.168.10.1
255.255.255.0
```

Configure the interface facing Network B as:

```text
192.168.20.1
255.255.255.0
```

Make sure both router interfaces are:

> **Enabled / On**

---

# Step 17 — Configure PC-C

Use:

```text
IP:
192.168.20.10

Mask:
255.255.255.0

Gateway:
192.168.20.1
```

---

# Step 18 — Configure Gateways

PC-A:

```text
Gateway:
192.168.10.1
```

PC-B:

```text
Gateway:
192.168.10.1
```

---

# 📋 Final Addressing Table

| Device | IPv4 | Mask | Gateway |
|---|---|---|---|
| PC-A | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 |
| PC-B | 192.168.10.20 | 255.255.255.0 | 192.168.10.1 |
| R-01 LAN A | 192.168.10.1 | 255.255.255.0 | — |
| R-01 LAN B | 192.168.20.1 | 255.255.255.0 | — |
| PC-C | 192.168.20.10 | 255.255.255.0 | 192.168.20.1 |

---

# Step 19 — Test Local Communication

From PC-A:

```cmd
ping 192.168.10.20
```

Record:

```text
PASS / FAIL
```

---

# Step 20 — Test the Gateway

From PC-A:

```cmd
ping 192.168.10.1
```

Record:

```text
PASS / FAIL
```

---

# Step 21 — Test Remote Communication

From PC-A:

```cmd
ping 192.168.20.10
```

Record:

```text
PASS / FAIL
```

If correctly configured, the traffic should travel:

```text
PC-A
 ↓
SW-A
 ↓
R-01
 ↓
SW-B
 ↓
PC-C
```

---

# 🔬 Step 22 — Simulation Mode

Switch Packet Tracer to:

> **Simulation Mode**

Generate traffic from:

```text
PC-A
```

to:

```text
PC-C
```

Use:

> **Capture / Forward**

Observe the traffic crossing R-01.

---

# 🧠 Question

Why is the router required?

```text
____________________________________________________

____________________________________________________
```

Expected concept:

> PC-A and PC-C belong to different IPv4 networks.

---

# 💥 PART 4 — TROUBLESHOOTING

# Challenge 1 — Wrong Gateway

Change PC-A's gateway to:

```text
192.168.10.254
```

Test:

```cmd
ping 192.168.10.20
```

Then:

```cmd
ping 192.168.20.10
```

Record:

| Test | Result |
|---|---|
| PC-A → PC-B | PASS / FAIL |
| PC-A → PC-C | PASS / FAIL |

---

# 🧠 Explain

Why can local communication still work?

```text
____________________________________________________
```

Why does remote communication fail?

```text
____________________________________________________
```

Restore:

```text
192.168.10.1
```

---

# 💥 Challenge 2 — Wrong IPv4 Network

Change PC-B to:

```text
192.168.30.20
```

while leaving:

```text
255.255.255.0
```

Test from PC-A:

```cmd
ping 192.168.30.20
```

What happens?

```text
PASS / FAIL
```

---

# 🧠 Why?

Although PC-A and PC-B are connected to the same switch, their configured IPv4 addresses now place them in different /24 networks.

This reinforces:

> **Physical connection does not automatically mean same IP network.**

Restore PC-B:

```text
192.168.10.20
```

---

# 💥 Challenge 3 — Duplicate IPv4 Address

Temporarily configure PC-B as:

```text
192.168.10.10
```

PC-A already uses:

```text
192.168.10.10
```

What problem did you create?

> **Duplicate IPv4 address**

This can cause unpredictable communication.

Restore:

```text
PC-B:
192.168.10.20
```

---

# 💥 Challenge 4 — Network Address

Would this be a normal valid host address on:

```text
192.168.10.0/24
```

?

```text
192.168.10.0
```

### YES / NO

> **NO**

That's the network address.

---

# 💥 Challenge 5 — Broadcast Address

Would this normally be assigned to a host on:

```text
192.168.10.0/24
```

?

```text
192.168.10.255
```

### YES / NO

> **NO**

That's the broadcast address.

---

# 💥 Challenge 6 — Private or Public?

Identify each:

### `10.25.50.10`

```text
PRIVATE / NOT RFC 1918 PRIVATE
```

### `172.20.10.50`

```text
PRIVATE / NOT RFC 1918 PRIVATE
```

### `172.40.10.50`

```text
PRIVATE / NOT RFC 1918 PRIVATE
```

### `192.168.100.50`

```text
PRIVATE / NOT RFC 1918 PRIVATE
```

### `8.8.8.8`

```text
PRIVATE / NOT RFC 1918 PRIVATE
```

Answers:

```text
10.25.50.10
PRIVATE

172.20.10.50
PRIVATE

172.40.10.50
NOT RFC 1918 PRIVATE

192.168.100.50
PRIVATE

8.8.8.8
NOT RFC 1918 PRIVATE
```

---

# 🧠 Knowledge Check

### 1.

How many bits are in IPv4?

### 2.

How many octets are in IPv4?

### 3.

What is `/24` in dotted-decimal notation?

### 4.

What is the network address for `192.168.50.0/24`?

### 5.

What is the broadcast address?

### 6.

What is the usable host range?

### 7.

What does `127.0.0.1` test?

### 8.

What does `169.254.x.x` commonly indicate on Windows?

### 9.

Why does a host need a default gateway?

### 10.

Can two hosts normally share the same IPv4 address on the same network?

---

# ✅ Answers

1. **32**
2. **4**
3. **255.255.255.0**
4. **192.168.50.0**
5. **192.168.50.255**
6. **192.168.50.1–192.168.50.254**
7. **Local loopback/TCP-IP stack**
8. **IPv4 link-local/APIPA; investigate expected DHCP configuration**
9. **To reach other IP networks**
10. **No**

---

# 🎓 Network+ Challenge

A workstation receives:

```text
169.254.100.25
```

when it should receive an address from DHCP.

What should you investigate first?

### A. Monitor
### B. DHCP connectivity/configuration
### C. HTTPS certificate
### D. DNS suffix only

> **Answer: B**

---

# 🎓 Network+ Challenge 2

A PC has:

```text
192.168.10.25/24
```

Which address is on the same subnet?

### A. `192.168.10.100`
### B. `192.168.20.25`
### C. `10.0.0.25`
### D. `172.16.10.25`

> **Answer: A**

---

# 🎓 Network+ Challenge 3

Which address should not normally be assigned to a host on `192.168.10.0/24`?

### A. `192.168.10.25`
### B. `192.168.10.100`
### C. `192.168.10.254`
### D. `192.168.10.255`

> **Answer: D**

`192.168.10.255` is the broadcast address.

---

# 📋 Lab Review

In this lab, you:

- Examined your Windows IPv4 configuration
- Identified DHCP status
- Used `ipconfig`
- Used `Get-NetIPConfiguration`
- Used `Get-NetIPAddress`
- Tested loopback
- Tested your gateway
- Tested a remote IP
- Tested DNS resolution
- Identified private addressing
- Recognized APIPA
- Built a /24 LAN
- Identified network, host, and broadcast addresses
- Built a second IPv4 network
- Configured a router
- Configured default gateways
- Tested routed communication
- Used Simulation Mode
- Troubleshot a wrong gateway
- Troubleshot a wrong network
- Created and corrected a duplicate address
- Identified private IPv4 ranges

---

# 💾 Save Your Packet Tracer Lab

Save the completed lab locally as:

```text
lab-07-ipv4-addressing.pkt
```

---

# 🏆 Lab Complete

You should now be able to look at:

```text
192.168.10.25/24
```

and understand considerably more than simply:

> "That's an IP address."

You should begin thinking:

```text
IPv4 Address
      ↓
Subnet
      ↓
Local or Remote?
      ↓
Gateway Needed?
      ↓
How Will Traffic Travel?
```

That's exactly the thinking we need for the next lesson.

---

# 📍 Course Progress

```text
🔵 PHASE 2 — ADDRESSING & COMMUNICATION

✅ Lesson 06 — Ethernet & MAC Addressing
✅ Lab 06

✅ Lesson 07 — IPv4 Addressing
✅ Lab 07

        ↓

🟡 NEXT:
Lesson 08 — Subnetting Fundamentals
        ↓
⬜ Lab 08 — Subnetting Fundamentals
        ↓
⬜ Lesson 09 — IPv6 Fundamentals
        ↓
⬜ Lesson 10 — TCP, UDP, Ports & Protocols
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 08 — Subnetting Fundamentals**

You'll take networks such as:

```text
192.168.10.0/24
```

and learn how to divide them into smaller networks.

You'll learn:

- Binary basics
- Prefix lengths
- Subnet masks
- Host bits
- Network bits
- Block sizes
- Number of subnets
- Number of hosts
- Network addresses
- Broadcast addresses
- Usable ranges
- How to solve subnetting questions

Don't worry if subnetting looks intimidating.

We'll build it one piece at a time.

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**