# Lab 11 --- IPv4 Addressing

## Lab Objective

Inspect real IPv4 configuration and build a small Packet Tracer network
while practicing private addresses, gateways, loopback, and common
addressing failures.

------------------------------------------------------------------------

# Part 1 --- Inspect Windows IPv4

Run:

``` powershell
Get-NetIPConfiguration
```

Then:

``` powershell
Get-NetIPAddress -AddressFamily IPv4
```

Record only non-sensitive training notes.

``` text
IPv4 address: ____________________________
Prefix length: ___________________________
Default gateway: _________________________
```

Do not publish organizational addressing information.

------------------------------------------------------------------------

# Part 2 --- Command Prompt Comparison

Run:

``` text
ipconfig /all
```

Find:

``` text
IPv4 Address
Subnet Mask
Default Gateway
DHCP Enabled
DNS Servers
```

Which fields overlap with PowerShell?

``` text
____________________________________________________
```

------------------------------------------------------------------------

# Part 3 --- Loopback Test

Run:

``` text
ping 127.0.0.1
```

What does a successful response demonstrate?

``` text
____________________________________________________
```

Does it prove your Ethernet or Wi-Fi connection works?

``` text
Yes / No
```

------------------------------------------------------------------------

# Part 4 --- Identify Address Types

Classify:

``` text
10.10.10.5        __________________
172.20.50.10      __________________
192.168.1.25      __________________
127.0.0.1         __________________
169.254.20.50     __________________
```

Use:

``` text
Private
Loopback
APIPA / Link-local
```

------------------------------------------------------------------------

# Part 5 --- Build a LAN

Packet Tracer:

``` text
PC0 ──┐
PC1 ──┼── Switch ── Router
PC2 ──┘
```

Configure the router LAN interface:

``` text
192.168.111.1 /24
```

Configure:

``` text
PC0  192.168.111.10 /24
PC1  192.168.111.20 /24
PC2  192.168.111.30 /24
```

Default gateway:

``` text
192.168.111.1
```

------------------------------------------------------------------------

# Part 6 --- Test the LAN

From PC0:

``` text
ping 192.168.111.20
ping 192.168.111.30
ping 192.168.111.1
```

Record results.

------------------------------------------------------------------------

# Part 7 --- Identify Special Addresses

For:

``` text
192.168.111.0/24
```

Fill in:

``` text
Network address: _______________________
First usable host: _____________________
Last usable host: ______________________
Broadcast address: _____________________
```

------------------------------------------------------------------------

# Part 8 --- Wrong Network

Change PC2 to:

``` text
192.168.112.30 /24
```

Keep the physical connection unchanged.

Test from PC0.

Record:

``` text
Physical link working? _________________
Same IP network? _______________________
Ping result: ___________________________
OSI layer involved: ____________________
```

Restore PC2.

------------------------------------------------------------------------

# Part 9 --- Duplicate IP

In the isolated Packet Tracer lab only, temporarily assign PC1 and PC2
the same address.

Observe what happens.

Record:

``` text
Duplicate address used: _________________
Observed behavior: ______________________
```

Restore unique addresses immediately.

------------------------------------------------------------------------

# Part 10 --- Missing Gateway

Remove PC0's default gateway.

Can PC0 still communicate with PC1 on the same local subnet?

``` text
Yes / No
```

Would PC0 normally need a gateway to reach another IP network?

``` text
Yes / No
```

Explain the difference.

------------------------------------------------------------------------

# Part 11 --- APIPA Scenario

A help-desk ticket says:

> "My computer has 169.254.44.18 and cannot reach company resources."

What would you suspect first?

``` text
____________________________________________________
```

List three checks.

``` text
1. __________________________________
2. __________________________________
3. __________________________________
```

------------------------------------------------------------------------

# Knowledge Check

1.  What does `/24` mean?
2.  Which address is commonly used for loopback testing?
3.  What does APIPA commonly indicate?
4.  Does a local same-subnet host require the default gateway to talk to
    another local same-subnet host?
5.  Why should two hosts not share the same IPv4 address?

------------------------------------------------------------------------

# Challenge

Build a five-PC network using:

``` text
192.168.115.0/24
```

Choose valid unique addresses, configure a gateway, and document:

``` text
Network address
Broadcast address
Usable range
Each host IP
Gateway
```

Then create and repair:

``` text
One duplicate IP
One wrong subnet
One missing gateway
```

Save:

``` text
lab-11-ipv4-addressing.pkt
```

------------------------------------------------------------------------

# Lab Completion Checklist

-   [ ] Inspected Windows IPv4 configuration
-   [ ] Compared PowerShell and ipconfig
-   [ ] Tested loopback
-   [ ] Classified address types
-   [ ] Built IPv4 Packet Tracer LAN
-   [ ] Tested local/gateway communication
-   [ ] Identified network/broadcast addresses
-   [ ] Diagnosed wrong network
-   [ ] Tested duplicate IP in lab
-   [ ] Tested missing gateway
-   [ ] Troubleshot APIPA scenario
-   [ ] Completed knowledge check
-   [ ] Completed challenge

------------------------------------------------------------------------

# Lab Complete

You have completed **Lab 11 --- IPv4 Addressing**.

# Next Lesson

➡️ **[Lesson 12 --- Subnet Masks and
CIDR](../lessons/lesson-12-subnet-masks-and-cidr.md)**
