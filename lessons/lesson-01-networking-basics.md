[lesson-01-networking-basics.md](https://github.com/user-attachments/files/31529532/lesson-01-networking-basics.md)
# Lesson 01 — Networking Basics

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain what a computer network is.
- Identify common devices found on a network.
- Explain the basic purpose of switches, routers, wireless access points, and firewalls.
- Distinguish between clients and servers.
- Explain the difference between a LAN and a WAN.
- Identify basic network information such as an IP address, subnet mask, default gateway, and DNS server.
- Use basic Windows and PowerShell commands to inspect your computer's network configuration.
- Build and test a simple network in Cisco Packet Tracer.

---

# What Is a Network?

A computer network is a group of devices that can communicate with one another.

Devices on a network can include:

```text
Desktop computers
Laptops
Servers
Printers
Phones
Tablets
Switches
Routers
Wireless access points
Firewalls
Internet-connected devices
```

Networks allow devices to share resources and communicate.

Examples include:

```text
Opening a website
Sending email
Printing to a network printer
Accessing a shared folder
Connecting to Microsoft 365
Using a VoIP phone
Connecting to a server
```

---

# A Simple Network

A very small network might look like:

```text
PC1 ─────┐
         │
PC2 ── Switch ── Router ── Internet
         │
Printer ─┘
```

Each device has a role.

As networks grow, more switches, routers, wireless access points, servers, and security devices may be added.

---

# Clients and Servers

Two important networking concepts are **clients** and **servers**.

## Client

A client requests a service or resource.

Examples:

```text
Laptop opening a website
PC requesting an IP address
User opening a shared file
Phone connecting to email
```

## Server

A server provides a service or resource.

Examples:

```text
Web server
DNS server
DHCP server
File server
Print server
Database server
```

A computer can sometimes act as both a client and a server depending on what it is doing.

---

# Common Network Devices

## Switch

A switch connects devices on the same local network.

Example:

```text
PC ─────┐
        │
PC ── Switch
        │
Printer ┘
```

Switches primarily forward Ethernet traffic between devices.

Later lessons will explain MAC addresses, switching tables, VLANs, and trunks.

---

# Router

A router connects different networks.

A common home or small-business example is:

```text
Local Network
     │
   Router
     │
  Internet
```

Routers make forwarding decisions using IP addresses and routing information.

Later lessons will cover routing in detail.

---

# Wireless Access Point

A wireless access point allows wireless devices to connect to a network.

Examples include:

```text
Laptop
Phone
Tablet
Wireless scanner
```

Conceptually:

```text
Laptop )))
          \
Phone )))  Access Point ── Network
          /
Tablet )))
```

Many home wireless routers combine several functions into one device, including routing, switching, and wireless access.

---

# Firewall

A firewall controls network traffic according to security rules.

It can allow or block traffic based on factors such as:

```text
Source
Destination
Protocol
Port
Connection state
Security policy
```

A firewall may be software running on a computer or a dedicated network/security device.

---

# Network Interface Card

A device needs a network interface to communicate on a network.

You may see terms such as:

```text
NIC
Network adapter
Ethernet adapter
Wi-Fi adapter
```

On Windows, PowerShell can display adapters with:

```powershell
Get-NetAdapter
```

---

# LAN and WAN

## LAN — Local Area Network

A LAN normally covers a limited area such as:

```text
Home
Office
Building
School
Small campus
```

Example:

```text
PC ── Switch ── Server
```

## WAN — Wide Area Network

A WAN connects networks across larger geographic areas.

Example:

```text
Office A ── WAN / Internet ── Office B
```

The Internet is the largest example of interconnected networks.

---

# Wired and Wireless Networks

## Wired

Wired Ethernet networks commonly use copper or fiber cabling.

Advantages can include:

```text
Reliable connections
Predictable performance
High speeds
Lower wireless interference
```

## Wireless

Wireless networking uses radio signals instead of a cable to the client.

Advantages include:

```text
Mobility
Convenience
Easy client connectivity
```

Real environments commonly use both.

---

# Basic Network Information

When troubleshooting a computer, several values are especially important.

## IP Address

An IP address identifies a device/interface for IP communication.

Example:

```text
192.168.1.25
```

## Subnet Mask

The subnet mask helps determine which part of an IPv4 address represents the network and which part represents the host.

Example:

```text
255.255.255.0
```

Subnetting is covered in detail later.

## Default Gateway

The default gateway is normally the router used to reach destinations outside the local subnet.

Example:

```text
192.168.1.1
```

## DNS Server

DNS translates names into IP addresses.

For example:

```text
example.com
        ↓
IP address
```

Without working DNS, you may be able to reach a destination by IP address but fail when using its hostname.

---

# DHCP

DHCP stands for:

```text
Dynamic Host Configuration Protocol
```

DHCP can automatically provide clients with information such as:

```text
IP address
Subnet mask
Default gateway
DNS servers
```

Without DHCP, network settings may need to be configured manually.

DHCP receives its own lesson later in the course.

---

# MAC Addresses

Network adapters also have a hardware address commonly called a **MAC address**.

Example format:

```text
00-1A-2B-3C-4D-5E
```

MAC addresses are important to Ethernet and switching.

You will work with them in later lessons.

---

# Inspect Your Windows Network

Open Command Prompt and run:

```text
ipconfig
```

For more detail:

```text
ipconfig /all
```

Look for:

```text
IPv4 Address
Subnet Mask
Default Gateway
DNS Servers
Physical Address
DHCP Enabled
```

Do not worry about understanding every line yet.

---

# Inspect Your Network with PowerShell

PowerShell provides structured networking information.

Run:

```powershell
Get-NetAdapter
```

Then:

```powershell
Get-NetIPConfiguration
```

For additional IP configuration:

```powershell
Get-NetIPAddress
```

PowerShell objects make this information useful for later automation and reporting.

---

# Test the Local TCP/IP Stack

Run:

```text
ping 127.0.0.1
```

`127.0.0.1` is the IPv4 loopback address.

It refers back to the local computer.

This test does **not** prove that the Internet or another device is reachable.

---

# Test Another Device

If you know your default gateway, you can often test it:

```text
ping <default-gateway>
```

Example:

```text
ping 192.168.1.1
```

A successful reply can provide useful troubleshooting information, although devices can be configured not to respond to ping.

---

# Test Internet Connectivity

A common test is:

```text
ping 8.8.8.8
```

Then compare it with a name-based test:

```text
ping example.com
```

These tests can help you begin separating:

```text
IP connectivity problems
        from
Name-resolution problems
```

You will learn a structured troubleshooting process later.

---

# Packet Tracer in This Course

Cisco Packet Tracer lets us practice networking without physical routers and switches.

Throughout the course, Packet Tracer labs will gradually introduce:

```text
PCs
Switches
Routers
Servers
Wireless devices
VLANs
Routing
DHCP
DNS
ACLs
```

Lesson 01 starts with a very small network.

---

# Network Troubleshooting Mindset

A useful networking habit is:

> Do not immediately change settings. First determine what is working and what is not.

For example:

```text
Does the network adapter work?
        ↓
Does the computer have an IP address?
        ↓
Can it reach the local network?
        ↓
Can it reach the default gateway?
        ↓
Can it reach an outside IP?
        ↓
Does DNS work?
```

Later lessons will turn this into a more complete troubleshooting process.

---

# Common Beginner Mistakes

## Router and Switch Are the Same Thing

They perform different networking roles.

A switch generally connects devices within a LAN.

A router connects different IP networks.

## Wi-Fi Means Internet

Wi-Fi is a method of connecting to a network.

A device can have a working Wi-Fi connection while the Internet connection is unavailable.

## Ping Proves Everything Works

Ping tests specific connectivity using ICMP.

A successful ping does not prove that every application or service works.

## Memorizing Without Testing

Networking becomes much easier when you combine the concepts with Packet Tracer, Wireshark, and real command-line tools.

---

# Key Takeaways

- A network allows devices to communicate and share resources.
- Clients request services; servers provide services.
- Switches connect devices on local Ethernet networks.
- Routers connect different IP networks.
- Wireless access points connect wireless clients to a network.
- Firewalls control traffic according to security rules.
- Important host settings include the IP address, subnet mask, default gateway, and DNS server.
- DHCP can automatically provide network configuration.
- Windows and PowerShell include useful networking tools.
- Good troubleshooting begins by gathering information before making changes.

---

# Lab

Continue to:

[Lab 01 — Networking Basics](../labs/lab-01-networking-basics.md)

---

# Additional Resources

**Cisco Packet Tracer:**  
https://www.netacad.com/cisco-packet-tracer

**Wireshark:**  
https://www.wireshark.org/

**Microsoft — Get-NetAdapter:**  
https://learn.microsoft.com/powershell/module/netadapter/get-netadapter

**Microsoft — Get-NetIPConfiguration:**  
https://learn.microsoft.com/powershell/module/nettcpip/get-netipconfiguration

**Microsoft — ipconfig:**  
https://learn.microsoft.com/windows-server/administration/windows-commands/ipconfig

**Microsoft — ping:**  
https://learn.microsoft.com/windows-server/administration/windows-commands/ping
