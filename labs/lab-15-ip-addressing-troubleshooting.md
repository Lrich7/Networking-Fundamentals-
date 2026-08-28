# Lab 15 --- IP Addressing Troubleshooting

## Lab Objective

Use Windows tools and Packet Tracer to diagnose realistic IPv4/IPv6
addressing problems before completing the Section 3 capstone project.

------------------------------------------------------------------------

# Part 1 --- Build Your Troubleshooting Toolkit

Review:

``` powershell
Get-NetAdapter
Get-NetIPConfiguration
Get-NetIPAddress
Get-NetNeighbor
Resolve-DnsName example.com
Test-NetConnection example.com -Port 443
```

Command Prompt:

``` text
ipconfig /all
ping
arp -a
nslookup
tracert
```

Write what each tool helps answer.

------------------------------------------------------------------------

# Part 2 --- Inspect Your Current Configuration

Without changing production settings, inspect:

``` text
Adapter
IPv4
Prefix
Gateway
DNS
IPv6
```

Do not publish real organizational details.

------------------------------------------------------------------------

# Part 3 --- Build the Troubleshooting Network

Packet Tracer:

``` text
PC0 ── Switch0 ── Router ── Switch1 ── PC2
PC1 ──┘                       └── PC3
```

Use:

``` text
LAN A: 192.168.150.0/26
LAN B: 192.168.150.64/26
```

Suggested router addresses:

``` text
LAN A gateway: 192.168.150.1
LAN B gateway: 192.168.150.65
```

Choose valid host addresses.

Verify all four PCs can communicate appropriately.

Save a working baseline before breaking anything.

------------------------------------------------------------------------

# Part 4 --- Ticket 1: Wrong Subnet

Break PC1 by assigning an address from LAN B while it remains physically
connected to LAN A.

Ticket:

> "PC1 is connected but cannot reach local resources."

Troubleshoot.

Document:

``` text
Symptom: __________________________________
Observed IP: ______________________________
Expected subnet: __________________________
Root cause: _______________________________
Fix: _____________________________________
Verification: _____________________________
```

------------------------------------------------------------------------

# Part 5 --- Ticket 2: Wrong Mask

Give PC0 an incorrect mask.

Do not immediately compare it with your notes.

Use your subnetting skills to determine the correct prefix.

Record the result.

------------------------------------------------------------------------

# Part 6 --- Ticket 3: Wrong Gateway

Give PC2 a gateway from the wrong subnet.

Test:

``` text
PC2 → PC3
PC2 → PC0
```

Explain why one may work while the other fails.

Repair it.

------------------------------------------------------------------------

# Part 7 --- Ticket 4: Duplicate IP

In the isolated lab, assign PC2 and PC3 the same address.

Observe the behavior.

Inspect ARP/MAC information if helpful.

Repair it and document the root cause.

------------------------------------------------------------------------

# Part 8 --- Ticket 5: APIPA Reasoning

You do not need to reproduce DHCP failure unless you want to.

Ticket:

``` text
IPv4 Address: 169.254.88.14
DHCP expected: Yes
```

Create a troubleshooting plan.

Include:

``` text
Physical/Wi-Fi connection
Correct network/VLAN
DHCP availability
DHCP relay/path
Client renewal/state
```

------------------------------------------------------------------------

# Part 9 --- Ticket 6: DNS vs. IP

Scenario:

``` text
Remote IP connectivity: Works
Hostname lookup: Fails
```

Which commands would you use?

``` text
____________________________________
```

Likely area:

``` text
____________________________________
```

------------------------------------------------------------------------

# Part 10 --- Ticket 7: IPv6

Add IPv6 to the two LANs using:

``` text
LAN A: 2001:db8:150:1::/64
LAN B: 2001:db8:150:2::/64
```

Verify IPv6 communication.

Then give one host an incorrect IPv6 prefix/network.

Diagnose and repair it.

------------------------------------------------------------------------

# Part 11 --- Troubleshooting Without Ping

Assume ICMP echo is blocked.

What other evidence can you use?

Examples:

``` text
ARP/neighbor information
Test-NetConnection
DNS resolution
Application connection
Interface state
Routing information
Packet Tracer Simulation Mode
```

Write a short plan.

------------------------------------------------------------------------

# Part 12 --- Create Your Ticket Template

Create a reusable template:

``` text
Ticket:
User/device:
Symptom:
Scope:
Expected configuration:
Observed configuration:
Tests:
Root cause:
Fix:
Verification:
Notes:
```

You can reuse this in later troubleshooting labs.

------------------------------------------------------------------------

# Knowledge Check

1.  What should you check when local traffic works but routed traffic
    fails?
2.  Why does APIPA point toward DHCP/path troubleshooting?
3.  What is a duplicate IP?
4.  How can DNS failure be separated from IP connectivity failure?
5.  Why should a working baseline be saved before creating lab faults?
6.  Why should you not rely only on ping?

------------------------------------------------------------------------

# Challenge

Have another person---or your future self---create three faults in the
Packet Tracer network without telling you which ones.

Possible faults:

``` text
Wrong IP
Wrong prefix
Wrong gateway
Duplicate IP
Disconnected link
Wrong IPv6 network
```

Troubleshoot using your ticket template.

Do not repair anything until you have documented the suspected root
cause.

Save:

``` text
lab-15-ip-troubleshooting.pkt
```

------------------------------------------------------------------------

# Lab Completion Checklist

-   [ ] Reviewed troubleshooting tools
-   [ ] Inspected current configuration safely
-   [ ] Built a working two-subnet baseline
-   [ ] Diagnosed wrong subnet
-   [ ] Diagnosed wrong mask
-   [ ] Diagnosed wrong gateway
-   [ ] Diagnosed duplicate IP
-   [ ] Created APIPA troubleshooting plan
-   [ ] Distinguished DNS from IP failure
-   [ ] Added/troubleshot IPv6
-   [ ] Planned troubleshooting without ping
-   [ ] Created reusable ticket template
-   [ ] Completed knowledge check
-   [ ] Completed challenge

------------------------------------------------------------------------

# Lab Complete

You have completed **Lab 15 --- IP Addressing Troubleshooting** and
**Section 3 --- IP Addressing & Subnetting**.

You now have hands-on experience with:

``` text
IPv4 addressing
Private addressing
Subnet masks
CIDR
Binary subnetting
Host calculations
Subnet design
Default gateways
IPv6 addressing
IPv6 neighbor discovery
APIPA
Duplicate IP troubleshooting
DNS vs. IP troubleshooting
Structured ticket documentation
```

Now apply those skills in Project 03.

------------------------------------------------------------------------

# 🛠️ Project 03 --- Address and Subnet a Growing Business

➡️ **[Project 03 --- Address and Subnet a Growing
Business](../projects/project-03-address-and-subnet-a-growing-business.md)**

This project gives you business requirements and requires you to design
the IPv4 addressing plan, build routed subnets, add IPv6, validate
connectivity, and troubleshoot addressing failures.

➡️ **[Begin Project 03 --- Address and Subnet a Growing
Business](../projects/project-03-address-and-subnet-a-growing-business.md)**
