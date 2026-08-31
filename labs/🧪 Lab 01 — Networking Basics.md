# 🧪 Lab 01 — Networking Basics

Welcome to your first **Networking Fundamentals Lab**.

In this lab, you'll examine the network configuration of your own Windows computer and perform several basic connectivity tests.

You are not expected to understand every value you see yet.

The goal is to become comfortable **finding networking information and beginning to understand what it means**.

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Identify your network adapters
- Determine which network adapter is currently active
- Find your IPv4 address
- Find your subnet mask
- Find your default gateway
- Identify your DNS servers
- Determine whether DHCP is enabled
- Test connectivity to your default gateway
- Test connectivity to an Internet IP address
- Test name resolution
- Use basic PowerShell networking commands
- Record and interpret your findings

---

# 🎓 Network+ Focus

This lab reinforces foundational concepts associated with **CompTIA Network+ N10-009**.

Pay particular attention to:

- Network interfaces
- IPv4 addressing
- Subnet masks
- Default gateways
- DNS
- DHCP
- ICMP
- Basic troubleshooting

You don't need to master these topics yet.

You'll study each one in more detail later in the course.

---

# 🧰 Tools Used

You'll use:

- 🪟 **Windows**
- ⌨️ **Command Prompt**
- 🔷 **PowerShell**

### Packet Tracer

🌐 **Not required for this lab.**

Cisco Packet Tracer will be introduced in **Lab 02 — Network Types and Topologies**.

---

# ⏱️ Estimated Time

Approximately:

**20–30 minutes**

Take your time and examine the results of each command.

---

# ⚠️ Before You Begin

This lab only uses commands that **view information or test connectivity**.

You will not be changing your network configuration.

> 💡 If you're completing this lab on a work computer, follow your organization's IT and security policies.

---

# 📋 Part 1 — Identify How You're Connected

Before running any commands, look at your computer.

Are you connected using:

- Ethernet
- Wi-Fi
- Both
- VPN
- Something else

Write down your answer.

```text
Connection Type:

____________________________
```

Now we'll verify that information using Windows.

---

# 🔷 Part 2 — View Your Network Adapters

Open **PowerShell**.

You can search for:

```text
PowerShell
```

from the Windows Start menu.

Run:

```powershell
Get-NetAdapter
```

You should see network adapters installed on your computer.

Example:

```text
Name       InterfaceDescription                Status
----       --------------------                ------
Ethernet   Realtek PCIe GbE Family Controller  Disconnected
Wi-Fi      Intel Wi-Fi Adapter                 Up
```

Your output will be different.

---

## 🔍 Examine the Results

Look for the **Status** column.

An adapter showing:

```text
Up
```

is currently active.

An adapter showing:

```text
Disconnected
```

exists but does not currently have an active connection.

---

## 📝 Record Your Findings

```text
Active Adapter:

____________________________

Adapter Type:

____________________________

Status:

____________________________
```

---

# 🧠 Question 1

Why might a computer have more than one network adapter?

Think about possibilities such as:

- Ethernet
- Wi-Fi
- VPNs
- Virtual machines
- Docking stations

Write your answer:

```text
____________________________________________________

____________________________________________________
```

---

# ⌨️ Part 3 — View Basic IP Configuration

Open **Command Prompt**.

Run:

```cmd
ipconfig
```

Find the adapter you're currently using.

Look for:

```text
IPv4 Address
Subnet Mask
Default Gateway
```

Example:

```text
IPv4 Address. . . . . . . . . . . : 192.168.1.25
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.1.1
```

Your values will probably be different.

---

# 📝 Record Your Configuration

```text
IPv4 Address:

____________________________

Subnet Mask:

____________________________

Default Gateway:

____________________________
```

---

# 🧠 Question 2

Which address identifies your computer on the IPv4 network?

```text
____________________________
```

---

# 🧠 Question 3

Which address would your computer normally use when sending traffic toward another network?

```text
____________________________
```

---

# 🔍 Part 4 — View Detailed Configuration

Now run:

```cmd
ipconfig /all
```

This displays much more information.

Find your active network adapter.

Look for:

```text
Description
Physical Address
DHCP Enabled
IPv4 Address
Subnet Mask
Default Gateway
DHCP Server
DNS Servers
```

---

# 📝 Record the Results

```text
Adapter Description:

____________________________________________

Physical Address:

____________________________________________

DHCP Enabled:

Yes / No

IPv4 Address:

____________________________________________

Subnet Mask:

____________________________________________

Default Gateway:

____________________________________________

DHCP Server:

____________________________________________

DNS Server(s):

____________________________________________
```

---

# 🔎 What Is the Physical Address?

The **Physical Address** shown by `ipconfig /all` is the adapter's **MAC address**.

It may look similar to:

```text
A4-B1-C1-12-34-56
```

We'll study MAC addresses in:

**Lesson 06 — Ethernet and MAC Addressing**

For now, simply recognize what the field represents.

---

# 🧠 Question 4

Is DHCP enabled on your active adapter?

```text
Yes / No
```

If yes, your computer is most likely receiving network configuration automatically.

We'll study DHCP in detail later.

---

# ⚠️ Check Your IPv4 Address

Look at the IPv4 address you recorded.

Does it begin with:

```text
169.254
```

If **no**, continue normally.

If **yes**, your computer may have assigned itself an **APIPA address** because it could not obtain expected IPv4 configuration through DHCP.

Do not change anything yet.

This is exactly the type of clue a network technician should notice.

---

# 🔷 Part 5 — View IP Configuration with PowerShell

Return to PowerShell.

Run:

```powershell
Get-NetIPConfiguration
```

Look for your active adapter.

You may see fields including:

```text
InterfaceAlias
InterfaceDescription
IPv4Address
IPv6DefaultGateway
IPv4DefaultGateway
DNSServer
```

Compare this output with what you saw using:

```cmd
ipconfig /all
```

---

# 🧠 Question 5

Did PowerShell and Command Prompt report the same IPv4 address?

```text
Yes / No
```

They should be examining the same underlying Windows networking configuration, even though the commands display it differently.

---

# 🔬 Part 6 — Examine Your IPv4 Address More Closely

Run:

```powershell
Get-NetIPAddress -AddressFamily IPv4
```

You may see several addresses.

Don't assume every address belongs to your main Internet connection.

You may see addresses associated with:

- Ethernet
- Wi-Fi
- Loopback
- VPN software
- Virtual machines
- Virtual switches

This is why identifying the **correct interface** matters during troubleshooting.

---

# 🧠 Question 6

Why might running a command show several IPv4 addresses?

```text
____________________________________________________

____________________________________________________
```

---

# 🚪 Part 7 — Test Your Default Gateway

Now you'll perform your first connectivity test.

Find the default gateway you recorded earlier.

Example:

```text
192.168.1.1
```

Run:

```cmd
ping YOUR-GATEWAY-IP
```

For example:

```cmd
ping 192.168.1.1
```

Do **not** automatically use `192.168.1.1`.

Use the actual default gateway shown on your computer.

---

# ✅ Successful Result

A successful result may look similar to:

```text
Reply from 192.168.1.1: bytes=32 time<1ms TTL=64
```

---

# ❌ Failed Result

A failed test might show:

```text
Request timed out.
```

or another error.

A failed ping does not automatically mean the gateway is offline.

Some devices or firewalls may not respond to ICMP echo requests.

---

# 📝 Record Your Result

```text
Default Gateway:

____________________________

Ping Successful?

Yes / No

Average Response Time:

____________________________
```

---

# 🧠 Question 7

What did this test attempt to determine?

```text
____________________________________________________

____________________________________________________
```

---

# 🌎 Part 8 — Test Internet Connectivity

Next, test connectivity to a public IP address.

Run:

```cmd
ping 8.8.8.8
```

`8.8.8.8` is a public Google DNS address commonly used for basic connectivity testing.

---

# 📝 Record the Result

```text
Ping Successful?

Yes / No

Average Response Time:

____________________________
```

---

# 🧠 Question 8

If you can successfully ping your gateway **and** `8.8.8.8`, what does that suggest?

```text
____________________________________________________

____________________________________________________
```

It provides evidence that IP connectivity beyond your local network is functioning for this test.

It does **not** prove every network service is working.

---

# 📖 Part 9 — Test Name Resolution

Now try:

```cmd
ping google.com
```

Notice something different.

You entered:

```text
google.com
```

instead of an IP address.

Windows must determine an IP address associated with that hostname before sending the ping traffic.

DNS normally performs that job.

---

# 📝 Record the Result

```text
Did google.com resolve to an IP address?

Yes / No

Resolved IP:

____________________________

Did the ping receive replies?

Yes / No
```

---

# 🧠 Question 9 — Troubleshooting Scenario

Imagine this happens:

```text
ping 8.8.8.8

SUCCESS
```

but:

```text
ping google.com

FAILS TO RESOLVE THE NAME
```

Which service would you investigate?

**A. DHCP**

**B. DNS**

**C. Ethernet**

**D. Bluetooth**

Your answer:

```text
____________________________
```

---

# 🔷 Part 10 — Test Connectivity with PowerShell

PowerShell has another useful networking tool:

```powershell
Test-NetConnection
```

Run:

```powershell
Test-NetConnection google.com
```

Look for information such as:

```text
ComputerName
RemoteAddress
InterfaceAlias
SourceAddress
PingSucceeded
```

---

# 📝 Record the Results

```text
ComputerName:

____________________________

RemoteAddress:

____________________________

InterfaceAlias:

____________________________

SourceAddress:

____________________________

PingSucceeded:

True / False
```

---

# 🧠 Question 10

Which field tells you which local network interface Windows used for the test?

```text
____________________________
```

---

# 🧪 Part 11 — Compare the Tools

You've now used several networking commands.

Complete the table.

| Command | What Did It Help You Find? |
|---|---|
| `Get-NetAdapter` | |
| `ipconfig` | |
| `ipconfig /all` | |
| `Get-NetIPConfiguration` | |
| `Get-NetIPAddress` | |
| `ping` | |
| `Test-NetConnection` | |

Don't worry about writing perfect definitions.

Describe what **you observed the command doing**.

---

# 🧠 Part 12 — Mini Troubleshooting Challenge

A user tells you:

> **"My Internet isn't working."**

You check the computer and discover:

```text
Wi-Fi Adapter: Up

IPv4 Address:
169.254.44.27

Default Gateway:
None
```

What stands out?

```text
____________________________________________________
```

What might you investigate next?

```text
____________________________________________________
```

---

# 🔎 Think It Through

The important clues are:

```text
169.254.x.x
```

and:

```text
No Default Gateway
```

The computer has an APIPA address and appears not to have received its expected IPv4 configuration.

At this point, you would begin investigating things such as:

- DHCP
- Network connectivity
- Wireless connectivity
- Adapter configuration

You wouldn't immediately start changing random settings.

You would gather more evidence first.

---

# 🧠 Part 13 — Another Troubleshooting Challenge

Consider this situation:

```text
Network Adapter:
Up

IPv4 Address:
192.168.1.25

Default Gateway:
192.168.1.1
```

Tests:

```text
ping 192.168.1.1
SUCCESS

ping 8.8.8.8
SUCCESS

ping example.com
NAME CANNOT BE RESOLVED
```

What is the most likely area to investigate?

```text
A. Ethernet cable

B. DNS

C. Network adapter

D. Default gateway
```

Your answer:

```text
____________________________
```

---

# 🧠 Part 14 — What Does Each Test Prove?

This is one of the most important concepts in the lab.

Suppose these tests succeed:

```text
Get-NetAdapter
     ↓
Adapter is Up

ping Default Gateway
     ↓
Success

ping 8.8.8.8
     ↓
Success

Resolve hostname
     ↓
Success
```

Each test provides another piece of evidence.

Think of troubleshooting like building a case.

```text
Observation
     ↓
Evidence
     ↓
More Testing
     ↓
Narrow Possibilities
     ↓
Find Root Cause
```

Avoid this:

```text
Problem
   ↓
Random Change
   ↓
Random Change
   ↓
Restart Everything
   ↓
Hope
```

Good troubleshooting is systematic.

---

# 📋 Part 15 — Build Your First Network Snapshot

Using the information you collected, create a simple snapshot of your current network configuration.

```text
Computer Network Snapshot
=========================

Connection Type:

____________________________________

Active Network Adapter:

____________________________________

IPv4 Address:

____________________________________

Subnet Mask:

____________________________________

Default Gateway:

____________________________________

DHCP Enabled:

____________________________________

DHCP Server:

____________________________________

DNS Server(s):

____________________________________

Gateway Ping:

PASS / FAIL

Internet IP Ping:

PASS / FAIL

Hostname Resolution:

PASS / FAIL

PowerShell Connectivity Test:

PASS / FAIL
```

> 🔐 **Privacy Note**
>
> This snapshot is for your own lab notes.
>
> Don't post sensitive company network information, public IP information, internal DNS details, or other organizational network information to a public GitHub repository.

---

# 🎯 Network+ Challenge

Answer these without looking back if possible.

### 1.

A Windows computer has the address:

```text
169.254.18.22
```

What should this make you suspect?

---

### 2.

A computer can ping its default gateway but cannot ping an Internet IP address.

Would DNS be your first suspect?

Why or why not?

---

### 3.

A computer can ping:

```text
8.8.8.8
```

but cannot resolve:

```text
example.com
```

What service should you investigate?

---

### 4.

Which device setting normally identifies where traffic should be sent when the destination is outside the local network?

---

### 5.

Which command provides detailed Windows IP configuration including DNS and DHCP information?

---

# ✅ Network+ Challenge Answers

### 1.

The computer may have failed to obtain expected IPv4 configuration through DHCP and assigned itself an APIPA address.

---

### 2.

Probably not.

The computer already has a problem reaching an outside IP address directly, so name resolution hasn't yet been shown to be the issue.

You would investigate connectivity beyond the local gateway first.

---

### 3.

**DNS**

---

### 4.

**Default gateway**

---

### 5.

```cmd
ipconfig /all
```

---

# 📝 Lab Review

You should now be able to recognize these pieces of information:

```text
Network Adapter
IPv4 Address
Subnet Mask
Default Gateway
DNS Server
DHCP
MAC Address
```

And you've used:

```text
ipconfig
ipconfig /all
ping
```

along with:

```powershell
Get-NetAdapter
Get-NetIPConfiguration
Get-NetIPAddress
Test-NetConnection
```

You aren't expected to know everything those commands can do yet.

The important thing is that you now know they exist and have used them yourself.

---

# 🧠 What You Just Accomplished

Without configuring a router or switch, you already performed a basic network investigation.

You:

```text
Identified the network interface
        ↓
Examined IP configuration
        ↓
Found the default gateway
        ↓
Found DNS information
        ↓
Identified DHCP status
        ↓
Tested local connectivity
        ↓
Tested Internet connectivity
        ↓
Tested name resolution
        ↓
Compared Windows networking tools
        ↓
Interpreted troubleshooting clues
```

That's the beginning of real network troubleshooting.

---

# 🌐 Packet Tracer Is Next

You did **not** need Cisco Packet Tracer for Lab 01.

That was intentional.

This lab focused on the network you're already using.

In the next lab, you'll begin working with simulated network environments using:

🌐 **Cisco Packet Tracer**

You'll start seeing how computers, switches, and other networking devices fit together.

---

# 🏁 Lab Complete

You've completed:

**🧪 Lab 01 — Networking Basics**

You should now have a basic understanding of how to inspect a Windows computer's network configuration and perform simple connectivity tests.

---

# ➡️ Next Lesson

Continue to:

➡️ **[Lesson 02 — Network Types and Topologies](../lessons/📘%20Lesson%2002%20—%20Network%20Types%20and%20Topologies.md)**

In Lesson 02, you'll learn about:

- LANs
- WANs
- WLANs
- PANs
- Other network types
- Client-server networks
- Peer-to-peer networks
- Star topology
- Mesh topology
- Other common network topologies

Then you'll use **Cisco Packet Tracer for the first time in Lab 02**.

---

# 📚 Return to Course

➡️ [Networking Lessons](../lessons/README.md)

➡️ [Networking Labs](README.md)