# Lab 04 --- OSI Model

## Lab Objective

Connect Windows troubleshooting tools and Packet Tracer observations to
the seven OSI layers.

## Part 1 --- Recall the Layers

Fill in:

``` text
7: __________________
6: __________________
5: __________________
4: __________________
3: __________________
2: __________________
1: __________________
```

## Part 2 --- Match Concepts

Assign a layer number to:

``` text
IP address ______
Ethernet frame ______
TCP port ______
Network cable ______
MAC address ______
Router ______
Traditional switch ______
HTTP ______
Bits/signals ______
```

## Part 3 --- Layer 1 Clues

Run:

``` powershell
Get-NetAdapter
```

Record adapter, status, and link speed. Which layer is most directly
related to the physical/link check?

## Part 4 --- Layer 3 Clues

Run:

``` powershell
Get-NetIPConfiguration
```

and:

``` text
ipconfig /all
```

Record IPv4 address, prefix/mask, and gateway. Do not publish company
network details.

## Part 5 --- Reachability

Test:

``` text
ping 127.0.0.1
ping <default-gateway>
ping 8.8.8.8
```

Remember that ICMP can be filtered.

## Part 6 --- Layer 4

Run:

``` powershell
Test-NetConnection example.com -Port 443
```

Record `RemoteAddress`, `RemotePort`, and `TcpTestSucceeded`.

## Part 7 --- Name Resolution

Run:

``` powershell
Resolve-DnsName example.com
```

or:

``` text
nslookup example.com
```

## Part 8 --- Packet Tracer

Build:

``` text
PC0 ── Switch ── PC1
```

Configure:

``` text
PC0 192.168.40.10 /24
PC1 192.168.40.20 /24
```

Ping PC1 from PC0. Save as `lab-04-osi-model.pkt`.

## Part 9 --- Simulation Mode

Observe a ping. Record source/destination IP and MAC addresses if
displayed by your Packet Tracer version.

``` text
Source IP: __________________
Destination IP: _____________
Source MAC: _________________
Destination MAC: ____________
```

## Part 10 --- Break Layer 1

Disconnect PC1's cable. Test again. Identify the first layer to
investigate. Reconnect and verify.

## Part 11 --- Break Layer 3

Change PC1 to `192.168.50.20/24` without adding a router. Test from PC0.
Identify the relevant layer. Restore `192.168.40.20/24`.

## Part 12 --- Bottom-Up Troubleshooting

Put in order: - Check cable/Wi-Fi/interface - Check local network -
Check IP configuration/routing - Test required port - Test
application/service

## Knowledge Check

1.  Which layer uses IP?
2.  Which layer uses TCP/UDP ports?
3.  Which layer uses MAC addresses?
4.  Which layer includes cables/signals?
5.  Why is OSI useful for troubleshooting?

## Challenge

Create an OSI troubleshooting checklist:

``` text
Layer 1: ____________________________
Layer 2: ____________________________
Layer 3: ____________________________
Layer 4: ____________________________
Layers 5–7: _________________________
```

## Lab Completion Checklist

-   [ ] Recalled seven layers
-   [ ] Mapped concepts
-   [ ] Inspected interface status
-   [ ] Inspected IP configuration
-   [ ] Tested reachability
-   [ ] Tested TCP 443
-   [ ] Tested DNS
-   [ ] Used Packet Tracer Simulation Mode
-   [ ] Broke/repaired Layer 1
-   [ ] Broke/repaired Layer 3
-   [ ] Completed knowledge check
-   [ ] Created troubleshooting checklist

# Lab Complete

You have completed **Lab 04 --- OSI Model**.

# Next Lesson

➡️ **[Lesson 05 --- TCP/IP
Model](../lessons/lesson-05-tcp-ip-model.md)**
