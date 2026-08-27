[lab-01-networking-basics.md](https://github.com/user-attachments/files/31529548/lab-01-networking-basics.md)
# Lab 01 — Networking Basics

## Lab Objective

Practice identifying your computer's basic network configuration and build your first working network in Cisco Packet Tracer.

By the end of this lab, you will have:

- Inspected a real Windows network adapter.
- Identified basic IP configuration.
- Tested local and network connectivity.
- Used PowerShell networking commands.
- Built a two-PC Packet Tracer network.
- Added a switch and tested a small LAN.
- Practiced basic troubleshooting.

---

# Part 1 — Identify Your Network Adapter

Open PowerShell.

Run:

```powershell
Get-NetAdapter
```

Locate the adapter you are currently using.

Record:

```text
Adapter Name:
____________________________________

Interface Description:
____________________________________

Status:
____________________________________

Link Speed:
____________________________________

MAC Address:
____________________________________
```

Is the connection:

```text
[ ] Ethernet
[ ] Wi-Fi
[ ] Other
```

---

# Part 2 — Inspect IP Configuration

Run:

```powershell
Get-NetIPConfiguration
```

You can also compare the result with:

```text
ipconfig /all
```

Record the active adapter's information:

```text
IPv4 Address:
____________________________________

Subnet Mask / Prefix:
____________________________________

Default Gateway:
____________________________________

DNS Server(s):
____________________________________

DHCP Enabled:
____________________________________
```

> Do not publish company or other sensitive network information in a public repository.

---

# Part 3 — Test Loopback

Run:

```text
ping 127.0.0.1
```

Record:

```text
Successful?
Yes / No
```

What does `127.0.0.1` represent?

```text
____________________________________________________
```

Does a successful loopback ping prove that your Internet connection works?

```text
____________________________________________________
```

---

# Part 4 — Test the Default Gateway

Find your default gateway from Part 2.

Run:

```text
ping <default-gateway>
```

Example:

```text
ping 192.168.1.1
```

Record:

```text
Successful?
Yes / No
```

If it fails, does that automatically prove the gateway is offline?

```text
____________________________________________________
```

Hint: Some devices are configured not to answer ICMP echo requests.

---

# Part 5 — Test Internet Connectivity

Run:

```text
ping 8.8.8.8
```

Then:

```text
ping example.com
```

Record:

```text
8.8.8.8 successful?
Yes / No

example.com successful?
Yes / No
```

What additional function must work for `example.com` to be translated into an IP address?

```text
____________________________________________________
```

---

# Part 6 — Test with PowerShell

Run:

```powershell
Test-NetConnection 8.8.8.8
```

Then:

```powershell
Test-NetConnection example.com -Port 443
```

Review the output.

Find:

```text
RemoteAddress
RemotePort
InterfaceAlias
SourceAddress
TcpTestSucceeded
```

Which command gives you more structured troubleshooting information: a basic `ping` or `Test-NetConnection`?

```text
____________________________________________________
```

---

# Part 7 — Your First Packet Tracer Network

Open Cisco Packet Tracer.

Create:

```text
PC0 ---------------- PC1
```

Use two PCs and connect them with an appropriate Ethernet connection.

Configure:

## PC0

```text
IP Address: 192.168.10.10
Subnet Mask: 255.255.255.0
```

## PC1

```text
IP Address: 192.168.10.20
Subnet Mask: 255.255.255.0
```

You do not need a default gateway for this simple same-network test.

---

# Part 8 — Test Packet Tracer Connectivity

On PC0:

```text
Desktop
   ↓
Command Prompt
```

Run:

```text
ping 192.168.10.20
```

Record:

```text
Successful?
Yes / No
```

Then from PC1:

```text
ping 192.168.10.10
```

Save the Packet Tracer file as:

```text
lab-01-two-pc-network.pkt
```

---

# Part 9 — Add a Switch

Now build:

```text
PC0 ─────┐
         │
       Switch
         │
PC1 ─────┘
```

Connect both PCs to the switch.

Keep the same addresses:

```text
PC0: 192.168.10.10 /24
PC1: 192.168.10.20 /24
```

Wait for the links to become active.

Test:

```text
PC0 > ping 192.168.10.20
```

Save the new topology as:

```text
lab-01-switched-network.pkt
```

---

# Part 10 — Add a Third PC

Add:

```text
PC2
```

Configure:

```text
IP Address: 192.168.10.30
Subnet Mask: 255.255.255.0
```

Your topology should resemble:

```text
PC0 ─────┐
         │
PC1 ── Switch
         │
PC2 ─────┘
```

Test connectivity between all three PCs.

Complete:

```text
PC0 → PC1   [ ] Works
PC0 → PC2   [ ] Works
PC1 → PC2   [ ] Works
```

---

# Part 11 — Break the Network

Troubleshooting is easier to learn when something is intentionally broken.

Change PC2 to:

```text
IP Address: 192.168.20.30
Subnet Mask: 255.255.255.0
```

Do **not** add a router.

Try:

```text
PC0 > ping 192.168.20.30
```

Does it work?

```text
Yes / No
```

Why do you think the result changed?

```text
____________________________________________________

____________________________________________________
```

Do not worry if you cannot fully explain the subnetting yet. This is a preview of concepts covered later.

Restore PC2 to:

```text
192.168.10.30
255.255.255.0
```

Verify that connectivity returns.

---

# Part 12 — Packet Tracer Simulation Mode

Switch Packet Tracer from:

```text
Realtime
```

to:

```text
Simulation
```

Send a ping between two PCs.

Watch the packet move through the network.

At this point, focus on the idea that network communication is made up of packets/frames moving between devices.

Later lessons will explain what is happening at each layer.

---

# Part 13 — Identify the Device

Match the device with its basic job.

```text
1. Switch
2. Router
3. Wireless Access Point
4. Firewall
5. Server
```

```text
___ Provides services or resources to clients

___ Connects different IP networks

___ Connects devices on a local Ethernet network

___ Allows wireless devices to connect to a network

___ Controls traffic according to security rules
```

---

# Part 14 — Troubleshooting Scenario

A user says:

> "My Wi-Fi says connected, but the Internet doesn't work."

Does the fact that Wi-Fi is connected prove that Internet access is working?

```text
Yes / No
```

List three things you might check before changing settings:

```text
1. ____________________________________

2. ____________________________________

3. ____________________________________
```

---

# Knowledge Check

## Question 1

Which device primarily connects devices on the same local Ethernet network?

A. Router  
B. Switch  
C. DNS server  
D. Firewall

## Question 2

Which device primarily connects different IP networks?

A. Router  
B. Switch  
C. Printer  
D. Access point

## Question 3

What normally helps a computer reach destinations outside its local subnet?

A. MAC address  
B. Default gateway  
C. Hostname  
D. Link speed

## Question 4

What service translates names such as `example.com` into IP addresses?

A. DHCP  
B. DNS  
C. ARP  
D. Ethernet

## Question 5

What can DHCP provide automatically?

A. IP configuration  
B. A physical network cable  
C. A MAC address for the NIC  
D. A switch port

## Question 6

What does `127.0.0.1` represent?

A. Default gateway  
B. Loopback address  
C. DNS server  
D. Broadcast address

## Question 7

Does a successful ping prove every application and network service works?

A. Yes  
B. No

---

# Challenge

Without looking back at the lesson, draw a simple network containing:

```text
3 PCs
1 switch
1 router
1 wireless access point
1 server
Internet
```

Label each device with its basic purpose.

You can draw it on paper, in your notes, or recreate it in Packet Tracer.

---

# Lab Completion Checklist

- [ ] Identified active network adapter
- [ ] Recorded IP configuration
- [ ] Tested loopback
- [ ] Tested default gateway
- [ ] Tested IP connectivity
- [ ] Tested DNS/name-based connectivity
- [ ] Used `Test-NetConnection`
- [ ] Built a two-PC Packet Tracer network
- [ ] Added a switch
- [ ] Added a third PC
- [ ] Intentionally broke and repaired connectivity
- [ ] Used Packet Tracer Simulation Mode
- [ ] Completed the knowledge check
- [ ] Saved Packet Tracer lab files

---

# Lab Complete

You have completed your first Networking Fundamentals lab.

You should now understand the basic roles of common network devices and know how to inspect and test a simple network.

---

# Next Lesson

[Lesson 02 — Network Types and Topologies](../lessons/lesson-02-network-types-and-topologies.md)
