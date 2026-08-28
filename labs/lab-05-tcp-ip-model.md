# Lab 05 --- TCP/IP Model

## Lab Objective

Use Windows tools and Packet Tracer to connect the TCP/IP model to real
communication and troubleshooting.

## Part 1 --- Recall TCP/IP

``` text
Layer 4: __________________
Layer 3: __________________
Layer 2: __________________
Layer 1: __________________
```

## Part 2 --- Map to OSI

``` text
OSI 7–5 → TCP/IP __________________
OSI 4   → TCP/IP __________________
OSI 3   → TCP/IP __________________
OSI 2–1 → TCP/IP __________________
```

## Part 3 --- Network Access

Run:

``` powershell
Get-NetAdapter
```

Record adapter, status, link speed, and MAC address.

## Part 4 --- Internet Layer

Run:

``` powershell
Get-NetIPConfiguration
```

Record IPv4 address, prefix, gateway, and DNS server. Do not publish
organizational details.

## Part 5 --- IP Tests

``` text
ping 127.0.0.1
ping 8.8.8.8
```

Record results. Remember that ICMP may be filtered.

## Part 6 --- DNS

Run:

``` powershell
Resolve-DnsName example.com
```

or `nslookup example.com`. Record one returned address.

## Part 7 --- Transport

Run:

``` powershell
Test-NetConnection example.com -Port 443
```

Record remote address, port, and `TcpTestSucceeded`.

## Part 8 --- Route

Run:

``` text
tracert example.com
```

Count visible hops. Not every router must respond.

## Part 9 --- Packet Tracer

Build:

``` text
PC0 ── Switch ── PC1
```

Configure:

``` text
PC0 192.168.50.10 /24
PC1 192.168.50.20 /24
```

Test connectivity and save as `lab-05-tcp-ip-model.pkt`.

## Part 10 --- Simulation

Observe a ping and identify IP and MAC information. Which belongs to the
Internet layer? Which belongs to Network Access?

## Part 11 --- Add a Server

Add:

``` text
Server 192.168.50.100 /24
```

Ping it from PC0. If the Packet Tracer server supports HTTP, enable HTTP
and browse from PC0 to `http://192.168.50.100`.

## Part 12 --- Break Network Access

Disconnect PC0. Test ping/application access. Identify the TCP/IP layer
to investigate first. Restore it.

## Part 13 --- Break the Internet Layer

Change PC1 to `192.168.60.20/24` without a router. Test, identify the
layer involved, then restore `192.168.50.20/24`.

## Part 14 --- Build Your Troubleshooting Flow

``` text
Network Access: ______________________________
Internet: ____________________________________
Transport: ___________________________________
Application: _________________________________
```

Think:

``` text
Connected?
  ↓
Addressed?
  ↓
Reachable?
  ↓
Port reachable?
  ↓
Application working?
```

## Knowledge Check

1.  Which TCP/IP layer contains TCP/UDP?
2.  Which layer contains IP?
3.  Which layer includes Ethernet/Wi-Fi?
4.  Which layer includes HTTP and DNS?
5.  What does `Test-NetConnection ... -Port 443` help test?
6.  If Ethernet is unplugged, where should troubleshooting start?

## Challenge

Document how you would troubleshoot: **"My computer is connected, but I
cannot reach a website."**

Use at least:

``` text
Get-NetAdapter
Get-NetIPConfiguration
ping
Resolve-DnsName / nslookup
Test-NetConnection
tracert
```

## Lab Completion Checklist

-   [ ] Recalled TCP/IP layers
-   [ ] Mapped TCP/IP to OSI
-   [ ] Inspected adapter/IP information
-   [ ] Tested IP
-   [ ] Tested DNS
-   [ ] Tested TCP 443
-   [ ] Used traceroute
-   [ ] Built Packet Tracer LAN
-   [ ] Used Simulation Mode
-   [ ] Added/tested server
-   [ ] Broke/repaired Network Access
-   [ ] Broke/repaired IP addressing
-   [ ] Completed troubleshooting flow
-   [ ] Completed knowledge check
-   [ ] Completed challenge

# Lab Complete

You have completed **Lab 05 --- TCP/IP Model** and the first section of
the course.

You now have experience with networking basics, types/topologies,
devices, OSI, TCP/IP, Windows/PowerShell tools, Packet Tracer, and
structured troubleshooting.

# 🛠️ Project 01 --- Build Your First Network

Now apply Lessons 01--05 without step-by-step lab guidance.

➡️ **[Project 01 --- Build Your First
Network](../projects/project-01-build-your-first-network.md)**

Use this workflow:

``` text
Understand requirement
   ↓
Design topology
   ↓
Choose devices
   ↓
Configure
   ↓
Test
   ↓
Document
   ↓
Break something
   ↓
Troubleshoot
   ↓
Repair and verify
```

➡️ **[Begin Project 01 --- Build Your First
Network](../projects/project-01-build-your-first-network.md)**
