# Lesson 15 --- IP Addressing Troubleshooting

## Learning Objectives

By the end of this lesson, you will be able to:

-   Use a repeatable process to troubleshoot IP addressing.
-   Identify incorrect IPv4 addresses, masks, gateways, and duplicate
    addresses.
-   Recognize APIPA as a DHCP-related clue.
-   Determine whether a failure is local, gateway-related,
    routing-related, or name-resolution-related.
-   Use Windows and PowerShell networking commands safely.
-   Distinguish IPv4 addressing problems from DNS problems.
-   Apply subnetting knowledge to troubleshooting tickets.
-   Document symptoms, causes, fixes, and verification.

------------------------------------------------------------------------

# Troubleshoot the Scope First

Before changing settings, determine:

``` text
One user or many?
One device or all devices?
Wired or wireless?
One subnet or multiple?
Local resources or Internet?
IP address or hostname?
IPv4, IPv6, or both?
```

Scope helps prevent random troubleshooting.

------------------------------------------------------------------------

# A Repeatable IPv4 Process

Use:

``` text
1. Check interface
2. Inspect IP configuration
3. Validate address
4. Validate subnet mask/prefix
5. Validate gateway
6. Test loopback
7. Test local IP
8. Test gateway
9. Test remote IP
10. Test DNS/name
11. Trace path if needed
12. Document
```

------------------------------------------------------------------------

# Step 1 --- Interface

``` powershell
Get-NetAdapter
```

Ask:

``` text
Up?
Disabled?
Cable/Wi-Fi connected?
Expected adapter?
```

------------------------------------------------------------------------

# Step 2 --- IP Configuration

``` powershell
Get-NetIPConfiguration
```

and:

``` text
ipconfig /all
```

Check:

``` text
IPv4 address
Prefix/mask
Gateway
DHCP status
DNS servers
```

------------------------------------------------------------------------

# Step 3 --- Look for APIPA

If you expected DHCP but see:

``` text
169.254.x.x
```

investigate:

``` text
Physical/Wi-Fi connectivity
Switch/VLAN path
DHCP availability
DHCP relay/path
Client DHCP state
```

Do not immediately assume the DHCP server itself is down.

------------------------------------------------------------------------

# Step 4 --- Validate the Subnet

Example:

``` text
PC:      192.168.150.70/26
Gateway: 192.168.150.1
```

A `/26` has blocks:

``` text
0–63
64–127
128–191
192–255
```

The PC is in:

``` text
192.168.150.64/26
```

The gateway `192.168.150.1` is not in that subnet.

That is a configuration problem.

------------------------------------------------------------------------

# Step 5 --- Test Loopback

``` text
ping 127.0.0.1
```

and optionally:

``` text
ping ::1
```

This verifies the local protocol stack, not the network path.

------------------------------------------------------------------------

# Step 6 --- Test the Local Address

Ping the host's own assigned IPv4 address if useful.

Then test another known local host.

------------------------------------------------------------------------

# Step 7 --- Test the Gateway

``` text
ping <default-gateway>
```

A failed ping is a clue, but remember ICMP may be filtered.

Combine ping with other evidence.

------------------------------------------------------------------------

# Step 8 --- Test a Remote IP

Example training target:

``` text
ping 8.8.8.8
```

If a remote IP works but a hostname fails, investigate DNS.

------------------------------------------------------------------------

# Step 9 --- Test DNS

``` powershell
Resolve-DnsName example.com
```

or:

``` text
nslookup example.com
```

If name resolution fails while remote IP connectivity works, the issue
may be DNS-related rather than basic IP routing.

------------------------------------------------------------------------

# Step 10 --- Test a Service Port

``` powershell
Test-NetConnection example.com -Port 443
```

This helps distinguish:

``` text
Basic IP reachability
        vs.
Specific TCP service reachability
```

------------------------------------------------------------------------

# Step 11 --- Trace the Path

``` text
tracert example.com
```

or PowerShell tools as appropriate.

Not every hop is guaranteed to answer.

------------------------------------------------------------------------

# Duplicate Address Clues

Possible clues:

``` text
Intermittent communication
ARP mappings changing unexpectedly
Address conflict warning
One device works after another disconnects
```

Commands that may help:

``` text
arp -a
```

``` powershell
Get-NetNeighbor -AddressFamily IPv4
```

------------------------------------------------------------------------

# Wrong Gateway

Symptoms can include:

``` text
Local subnet works
Remote networks fail
```

This is a classic clue.

------------------------------------------------------------------------

# Wrong Subnet Mask

A wrong mask can produce confusing behavior because the host may
incorrectly decide whether a destination is local or remote.

Always validate:

``` text
IP + Prefix + Gateway
```

as a set.

------------------------------------------------------------------------

# DNS Is Not the Same as IP Connectivity

Ticket:

> "The Internet is down."

Tests:

``` text
ping 8.8.8.8 → works
Resolve-DnsName example.com → fails
```

The network may have IP connectivity while DNS is failing.

Avoid calling every website problem an "Internet outage."

------------------------------------------------------------------------

# Document Your Work

Use:

``` text
Symptom
Scope
Expected configuration
Observed configuration
Tests performed
Root cause
Fix
Verification
```

This makes troubleshooting repeatable and useful to the next technician.

------------------------------------------------------------------------

# Key Terms

``` text
Scope
APIPA
Default Gateway
Subnet Mismatch
Duplicate IP
DNS
Reachability
Route Trace
Root Cause
Verification
```

------------------------------------------------------------------------

# Knowledge Check

1.  What does `169.254.x.x` suggest when DHCP was expected?
2.  If local resources work but remote networks fail, what configuration
    should you check?
3.  Why can a wrong subnet mask cause confusing failures?
4.  If `8.8.8.8` works but `example.com` does not resolve, what service
    should you investigate?
5.  Does failed ping always prove a host is down?
6.  Why should troubleshooting results be documented?

------------------------------------------------------------------------

# Lesson Summary

Use a structured process:

``` text
Interface
   ↓
IP / Mask
   ↓
Gateway
   ↓
Local
   ↓
Remote IP
   ↓
DNS
   ↓
Port / Application
   ↓
Document
```

Do not skip straight to changing settings.

------------------------------------------------------------------------

# Hands-On Lab

➡️ **[Lab 15 --- IP Addressing
Troubleshooting](../labs/lab-15-ip-addressing-troubleshooting.md)**
