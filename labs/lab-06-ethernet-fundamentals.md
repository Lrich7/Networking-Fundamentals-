# Lab 06 --- Ethernet Fundamentals

## Lab Objective

Inspect Ethernet information in Windows and use Cisco Packet Tracer to
observe switches, MAC addresses, frames, and local Ethernet
communication.

------------------------------------------------------------------------

# Part 1 --- Inspect Your Adapter

Open PowerShell:

``` powershell
Get-NetAdapter |
    Select-Object Name,
        InterfaceDescription,
        Status,
        MacAddress,
        LinkSpeed
```

Record:

``` text
Adapter: __________________________________
Status: ___________________________________
MAC Address: _______________________________
Link Speed: ________________________________
```

------------------------------------------------------------------------

# Part 2 --- Build an Ethernet LAN

In Packet Tracer create:

``` text
PC0 ──┐
PC1 ──┼── Switch
PC2 ──┘
```

Configure:

``` text
PC0  192.168.60.10 /24
PC1  192.168.60.20 /24
PC2  192.168.60.30 /24
```

------------------------------------------------------------------------

# Part 3 --- Record MAC Addresses

On each Packet Tracer PC, inspect its network information.

Record:

``` text
PC0 MAC: ______________________________
PC1 MAC: ______________________________
PC2 MAC: ______________________________
```

Compare these with the IP addresses.

------------------------------------------------------------------------

# Part 4 --- Generate Traffic

From PC0:

``` text
ping 192.168.60.20
```

Then:

``` text
ping 192.168.60.30
```

Verify both succeed.

------------------------------------------------------------------------

# Part 5 --- Inspect the Switch

Open the switch CLI.

Try:

``` text
show mac address-table
```

Record which MAC addresses appear and which ports they are associated
with.

``` text
MAC                     Port
________________________________________
________________________________________
________________________________________
```

------------------------------------------------------------------------

# Part 6 --- Simulation Mode

Switch to Simulation Mode.

Send a ping from PC0 to PC1.

Observe the first exchange and subsequent frames.

Look for:

``` text
Source MAC
Destination MAC
Source IP
Destination IP
```

Record what you observe.

------------------------------------------------------------------------

# Part 7 --- Unicast vs. Broadcast

In Simulation Mode, observe whether any initial traffic is sent broadly
before normal unicast communication occurs.

Do not worry if you do not fully understand ARP yet; Lesson 07 explains
it.

Write:

``` text
Broadcast observed? ______________________
Unicast observed? ________________________
```

------------------------------------------------------------------------

# Part 8 --- Break Ethernet

Disconnect PC2's Ethernet cable.

Test from PC0.

``` text
ping 192.168.60.30
```

Record:

``` text
Result: __________________________________
OSI layer to check first: _________________
TCP/IP layer to check first: ______________
```

Reconnect and verify.

------------------------------------------------------------------------

# Part 9 --- Compare Switch and Hub Conceptually

Answer:

``` text
Why does a switch make better forwarding decisions than a hub?

____________________________________________________

What information does the switch use?

____________________________________________________
```

------------------------------------------------------------------------

# Knowledge Check

1.  What does `Get-NetAdapter` show?
2.  What does a switch learn?
3.  Which address does Ethernet use for local frame forwarding?
4.  What is a broadcast?
5.  Which OSI layer should you investigate first when the Ethernet cable
    is unplugged?

------------------------------------------------------------------------

# Challenge

Build a five-PC switched Ethernet network.

Generate traffic among all PCs, then inspect:

``` text
show mac address-table
```

Document which MAC address appears on each switch port.

Save:

``` text
lab-06-ethernet-challenge.pkt
```

------------------------------------------------------------------------

# Lab Completion Checklist

-   [ ] Inspected Windows Ethernet information
-   [ ] Built a switched LAN
-   [ ] Recorded MAC addresses
-   [ ] Generated traffic
-   [ ] Inspected the switch MAC table
-   [ ] Used Simulation Mode
-   [ ] Observed local Ethernet communication
-   [ ] Broke and repaired an Ethernet connection
-   [ ] Completed knowledge check
-   [ ] Completed challenge

------------------------------------------------------------------------

# Lab Complete

You have completed **Lab 06 --- Ethernet Fundamentals**.

# Next Lesson

➡️ **[Lesson 07 --- MAC Addresses and
ARP](../lessons/lesson-07-mac-addresses-and-arp.md)**
