# Lab 07 --- MAC Addresses and ARP

## Lab Objective

Inspect MAC and ARP information in Windows and observe the ARP
request/reply process in Cisco Packet Tracer.

------------------------------------------------------------------------

# Part 1 --- Inspect Windows MAC Addresses

Run:

``` powershell
Get-NetAdapter |
    Select-Object Name, MacAddress, Status
```

Record your active adapter's MAC address.

``` text
____________________________________
```

------------------------------------------------------------------------

# Part 2 --- Inspect the ARP Cache

Run:

``` text
arp -a
```

Then:

``` powershell
Get-NetNeighbor -AddressFamily IPv4
```

Record one IPv4-to-MAC mapping if available.

``` text
IPv4: __________________________________
MAC: ___________________________________
```

Do not publish company network information.

------------------------------------------------------------------------

# Part 3 --- Build the Lab

Packet Tracer:

``` text
PC0 ──┐
      Switch
PC1 ──┘
```

Configure:

``` text
PC0 192.168.70.10 /24
PC1 192.168.70.20 /24
```

Record each MAC address.

------------------------------------------------------------------------

# Part 4 --- Observe ARP

Switch to Simulation Mode.

From PC0:

``` text
ping 192.168.70.20
```

Step through the events.

Look for an ARP request.

Record:

``` text
Requested IPv4: __________________________
Request destination: Broadcast / Unicast
```

------------------------------------------------------------------------

# Part 5 --- Observe the Reply

Continue through the simulation.

Record:

``` text
ARP reply source IPv4: ___________________
ARP reply source MAC: ____________________
```

Explain what PC0 learned:

``` text
____________________________________________________
```

------------------------------------------------------------------------

# Part 6 --- Inspect Learned Information

After communication, inspect PC0's ARP information using the Packet
Tracer tools available on the endpoint.

Also inspect the switch:

``` text
show mac address-table
```

Explain the difference:

``` text
ARP/neighbor table maps:
____________________________________

Switch MAC table maps:
____________________________________
```

------------------------------------------------------------------------

# Part 7 --- Add a Router

Add a router and configure the LAN-facing interface:

``` text
192.168.70.1 /24
```

Set PC0's gateway to:

``` text
192.168.70.1
```

Ping the gateway.

Observe which MAC address PC0 learns.

------------------------------------------------------------------------

# Part 8 --- Local vs. Remote Reasoning

Answer:

If PC0 sends traffic to a remote IP network, which local MAC address
does it normally use as the Ethernet destination?

``` text
____________________________________________________
```

Why?

``` text
____________________________________________________
```

------------------------------------------------------------------------

# Part 9 --- Troubleshooting Scenario

Suppose a PC can see its gateway's IP configuration but never learns a
usable neighbor mapping for it.

Which areas would you investigate?

``` text
Cable / Wi-Fi
Switch path
Correct subnet
Gateway interface
Duplicate/misconfigured addressing
```

Write your first three checks.

------------------------------------------------------------------------

# Knowledge Check

1.  What does ARP map?
2.  Why is the ARP request broadcast?
3.  What does the switch MAC table map?
4.  Is a remote web server's MAC address normally learned by your PC
    across the Internet?
5.  What protocol replaces ARP-style neighbor discovery in IPv6?

------------------------------------------------------------------------

# Challenge

Build three PCs and one router on a switch.

Use Simulation Mode to document:

``` text
ARP request
ARP reply
First ping
Second ping
```

Compare the first and second ping. Explain why the second exchange may
require less discovery traffic.

Save:

``` text
lab-07-arp-challenge.pkt
```

------------------------------------------------------------------------

# Lab Completion Checklist

-   [ ] Inspected Windows MAC addresses
-   [ ] Inspected ARP/neighbor information
-   [ ] Built the Packet Tracer LAN
-   [ ] Observed an ARP request
-   [ ] Observed an ARP reply
-   [ ] Compared ARP and switch MAC tables
-   [ ] Added/tested a gateway
-   [ ] Explained local vs. remote MAC behavior
-   [ ] Completed troubleshooting scenario
-   [ ] Completed knowledge check
-   [ ] Completed challenge

------------------------------------------------------------------------

# Lab Complete

You have completed **Lab 07 --- MAC Addresses and ARP**.

# Next Lesson

➡️ **[Lesson 08 --- Network Cables and
Connectors](../lessons/lesson-08-network-cables-and-connectors.md)**
