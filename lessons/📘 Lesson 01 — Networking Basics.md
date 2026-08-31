[📘 Lesson 01 — Networking Basics.md](https://github.com/user-attachments/files/31657721/Lesson.01.Networking.Basics.md)
# 📘 Lesson 01 — Networking Basics

Welcome to **Lesson 01 of Networking Fundamentals**.

This lesson starts with the most important question:

> **What is a network, and what is actually happening when devices communicate?**

You do not need previous networking experience for this lesson.

If you already work in IT, some of these concepts may feel familiar, but this lesson establishes the foundation we'll build on throughout the rest of the course.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain what a computer network is
- Explain why networks are used
- Identify common network resources
- Understand the difference between clients and servers
- Explain local and remote communication
- Understand the basic purpose of an IP address
- Understand the purpose of a network adapter
- Identify basic network information on a Windows computer
- Test basic connectivity
- Begin thinking about networking from a troubleshooting perspective

---

# 🎓 Network+ Focus

This lesson introduces concepts that support the **Networking Concepts** portion of CompTIA Network+.

Pay particular attention to:

- Network communication
- Clients and servers
- Network interfaces
- Local vs. remote resources
- IP addresses
- Default gateways
- DNS
- Basic connectivity testing

Don't worry about mastering all of these yet.

We'll revisit each topic in much greater detail later in the course.

---

# 🌐 What Is a Computer Network?

A **computer network** is a group of devices that can communicate with one another.

Devices on a network may include:

- Desktop computers
- Laptops
- Servers
- Printers
- Phones
- Tablets
- Switches
- Routers
- Wireless access points
- Cameras
- Smart devices
- Cloud services

At its simplest, a network allows one device to exchange information with another.

For example:

```text
Computer A
    │
    │ Network
    │
    ▼
Computer B
```

A real network usually contains many more devices.

```text
Computer ─┐
          │
Laptop ───┼── Switch ─── Router ─── Internet
          │
Printer ──┘
```

We'll learn what the switch and router do in later lessons.

For now, focus on the idea that the network provides a **path for communication**.

---

# 🧠 Why Do We Use Networks?

Without networks, computers would operate mostly as isolated devices.

Networks allow us to share resources and information.

Common examples include:

- Internet access
- Email
- Shared files
- Shared printers
- Websites
- Cloud applications
- Databases
- Microsoft 365
- Remote access
- Video meetings
- Authentication services
- Business applications

For example, when you open a shared file from a server, your computer communicates across the network to retrieve that file.

```text
Your Computer
     │
     ▼
   Network
     │
     ▼
File Server
     │
     ▼
Shared File
```

---

# 💻 Clients and Servers

Two terms you'll see constantly in networking are:

- **Client**
- **Server**

---

## 💻 Client

A **client** is usually a device or application requesting a service.

Examples include:

- Your laptop opening a website
- Outlook retrieving email
- A computer opening a shared file
- A phone connecting to a wireless network
- A workstation requesting an IP address

The client asks for something.

---

## 🖥️ Server

A **server** provides a service or resource.

Examples include:

- Web server
- File server
- Email server
- DNS server
- DHCP server
- Database server
- Authentication server

A simple client/server interaction looks like:

```text
CLIENT
"Can I have this webpage?"
        │
        ▼
      SERVER
"Yes. Here it is."
        │
        ▼
CLIENT
Displays webpage
```

The actual communication is much more complex, but this model is useful for understanding the basic relationship.

---

# 🔄 Client and Server Are Roles

A device is not always permanently one or the other.

The terms often describe the **role being performed during communication**.

For example, your computer might be a client when browsing a website.

But that same computer could also share a folder that another computer accesses.

In that situation, it is providing a resource.

---

# 🏠 Local vs. Remote Resources

A **local resource** exists directly on your computer.

Examples:

```text
C:\Users
C:\Documents
Installed applications
Local hard drive
```

A **remote resource** exists somewhere else and is accessed through a network.

Examples include:

```text
Shared network folder
Cloud application
Website
Network printer
File server
Remote desktop computer
```

If a resource is remote, networking must work correctly for you to reach it.

---

# 🏢 LAN vs. Internet Communication

Not all network communication goes to the Internet.

A device can communicate with another device inside the same organization or local network.

For example:

```text
PC ─── Switch ─── Printer
```

That communication may stay entirely inside the local network.

But opening a public website might look more like:

```text
PC
 │
 ▼
Switch
 │
 ▼
Router
 │
 ▼
Internet
 │
 ▼
Web Server
```

The path a packet takes depends on where the destination is located.

We'll study this much more deeply later.

---

# 🌎 Internet vs. Intranet

These terms are similar but mean different things.

## Internet

The **Internet** is the global collection of interconnected networks.

Examples include:

- Google
- Microsoft
- YouTube
- GitHub
- Public websites
- Cloud platforms

---

## Intranet

An **intranet** is a private network or private collection of resources used within an organization.

Examples could include:

- Internal SharePoint sites
- Internal company websites
- Internal documentation
- Employee portals
- Internal applications

An intranet usually isn't intended for unrestricted public access.

---

# 🔌 Network Interfaces

For a device to communicate on a network, it needs some kind of **network interface**.

Examples include:

```text
Ethernet adapter
Wi-Fi adapter
Virtual network adapter
VPN adapter
```

You may hear this referred to as a:

> **NIC — Network Interface Card**

Historically, this often referred to a physical expansion card installed in a computer.

Today, network interfaces are commonly built directly into laptops, desktops, servers, and other devices.

---

# 🪟 Looking at Your Own Network Interfaces

On Windows, PowerShell can display your network adapters.

Run:

```powershell
Get-NetAdapter
```

You might see something similar to:

```text
Name        InterfaceDescription               Status

Wi-Fi       Intel Wireless Adapter             Up
Ethernet    Realtek PCIe Ethernet Adapter      Disconnected
```

Don't worry about every column yet.

For now, notice:

- Adapter name
- Adapter type
- Connection status

---

# 🧾 Basic Network Configuration

Your computer needs information that tells it how to communicate.

Some of the most important pieces include:

```text
IP Address
Subnet Mask / Prefix
Default Gateway
DNS Server
```

You'll study each of these later.

For now, here is the high-level purpose of each.

---

## 📍 IP Address

An **IP address** identifies a device or network interface on an IP network.

Example:

```text
192.168.1.25
```

You can think of it as part of the information networks use to determine:

> **Where should this traffic go?**

This analogy isn't perfect, but an IP address is somewhat like an address used for delivering information to the correct destination.

---

# 🧱 Subnet Mask

The subnet mask helps determine which part of an IPv4 address identifies the **network** and which part identifies the **host**.

Example:

```text
255.255.255.0
```

You do not need to understand subnet masks yet.

We have an entire lesson dedicated to subnetting later.

For now, just recognize the term.

---

# 🚪 Default Gateway

The **default gateway** is normally the device your computer sends traffic to when the destination is outside its local network.

In many small networks, the default gateway is a router.

Example:

```text
PC
192.168.1.25
     │
     ▼
Default Gateway
192.168.1.1
     │
     ▼
Other Networks
```

A useful troubleshooting question later will be:

> **Can the computer reach its default gateway?**

---

# 📖 DNS Server

DNS stands for:

> **Domain Name System**

DNS helps translate names into IP addresses.

Humans prefer names like:

```text
github.com
```

Networks ultimately need addressing information such as:

```text
IP address
```

DNS helps connect the two.

We'll dedicate an entire lesson to DNS later.

---

# 🔍 Viewing Your Network Configuration

One of the most useful Windows networking commands is:

```cmd
ipconfig
```

Open Command Prompt and run:

```cmd
ipconfig
```

You may see something like:

```text
Wireless LAN adapter Wi-Fi:

   IPv4 Address. . . . . . . . . . . : 192.168.1.25
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1
```

Your actual addresses will likely be different.

---

# 🔎 More Detailed Information

Run:

```cmd
ipconfig /all
```

This shows much more information, including things such as:

- Adapter description
- Physical address
- DHCP status
- IPv4 address
- IPv6 address
- Default gateway
- DHCP server
- DNS servers
- Lease information

You aren't expected to understand all of it yet.

This course will gradually teach you how to read this output.

---

# 🔷 PowerShell Network Information

PowerShell provides another useful command:

```powershell
Get-NetIPConfiguration
```

This provides network configuration information in a structured PowerShell format.

You may see information about:

```text
InterfaceAlias
IPv4Address
IPv6Address
IPv4DefaultGateway
DNSServer
```

As your PowerShell skills improve, commands like this become very useful for administration and troubleshooting.

---

# 📡 Testing Connectivity with Ping

One of the most famous networking commands is:

```cmd
ping
```

`ping` can help determine whether a device can communicate with another IP host and whether ICMP echo traffic is answered.

For example:

```cmd
ping 8.8.8.8
```

You may see output similar to:

```text
Reply from 8.8.8.8: bytes=32 time=18ms TTL=117
```

This tells you that your computer received a response.

---

# 🧠 What Does Ping Actually Tell You?

Ping can provide useful evidence, but it doesn't automatically prove:

> **"The network is fine."**

For example, ping may fail because:

- The destination is offline
- Routing is broken
- A firewall blocks ICMP
- Your computer has incorrect addressing
- The gateway is unavailable
- The network connection is down

Likewise, ping may succeed while another application still fails.

A key troubleshooting principle is:

> **One successful test proves only what that specific test verified.**

This mindset becomes very important later.

---

# 🚪 Test Your Default Gateway

One useful first test is pinging your own default gateway.

First run:

```cmd
ipconfig
```

Find:

```text
Default Gateway
```

Then run:

```cmd
ping <gateway-address>
```

For example:

```cmd
ping 192.168.1.1
```

If you receive replies, your computer can at least communicate with that gateway using the tested path and protocol.

---

# 🌐 Test Internet Connectivity

You can also test connectivity to a known public IP address.

Example:

```cmd
ping 8.8.8.8
```

Then test a hostname:

```cmd
ping google.com
```

These tests provide different information.

If this works:

```cmd
ping 8.8.8.8
```

but this doesn't:

```cmd
ping google.com
```

you may begin investigating **DNS/name resolution**.

That's the beginning of troubleshooting by gathering evidence.

---

# 🧠 Think Like a Troubleshooter

Throughout this course, we'll constantly ask:

> **What do I know?**

> **What can I test?**

> **What does the result prove?**

Suppose a user tells you:

> "The Internet doesn't work."

Instead of immediately changing settings, gather information.

You might ask:

```text
Is Wi-Fi connected?

Does the computer have an IP address?

Does it have a default gateway?

Can it reach the gateway?

Can it reach an Internet IP address?

Can it resolve a hostname?

Is only one application affected?
```

Each answer narrows down the problem.

---

# 🔍 Example Troubleshooting Flow

A simplified investigation might look like:

```text
User cannot access website
        │
        ▼
Check network connection
        │
        ▼
Check IP configuration
        │
        ▼
Ping default gateway
        │
        ▼
Test outside IP
        │
        ▼
Test DNS resolution
        │
        ▼
Investigate application
```

This isn't the only troubleshooting process, but it demonstrates an important idea:

> **Move logically instead of randomly changing things.**

---

# ⚠️ The 169.254 Clue

You may eventually see an IPv4 address beginning with:

```text
169.254.x.x
```

Windows can automatically assign an address in this range when it cannot obtain normal IPv4 configuration through DHCP.

This is commonly called:

> **APIPA — Automatic Private IP Addressing**

You don't need to understand DHCP yet.

For now, remember this troubleshooting clue:

> **169.254.x.x often means you should investigate how the computer is obtaining its IP configuration.**

We'll revisit this later.

---

# 🗺️ A Simple Network

Consider this network:

```text
PC
192.168.1.25
      │
      ▼
    Switch
      │
      ▼
    Router
192.168.1.1
      │
      ▼
   Internet
```

The PC may need several things to communicate successfully:

```text
Working network adapter
        ↓
Valid IP address
        ↓
Correct subnet information
        ↓
Working default gateway
        ↓
Working DNS
        ↓
Working path to destination
```

If any important part fails, communication may be affected.

This course will teach you how to investigate each layer.

---

# 🧩 Networking Is a System

A common mistake when learning networking is trying to memorize every technology independently.

Instead, think about how the pieces work together.

For example:

```text
Application
     ↓
DNS
     ↓
TCP/UDP
     ↓
IP
     ↓
Ethernet/Wi-Fi
     ↓
Switch
     ↓
Router
     ↓
Destination
```

You don't need to understand that whole stack yet.

By the end of the course, you will.

---

# 🔧 Commands Introduced in This Lesson

You only need a few commands for now.

## Command Prompt

```cmd
ipconfig
ipconfig /all
ping
```

## PowerShell

```powershell
Get-NetAdapter
Get-NetIPConfiguration
```

Don't memorize output line by line.

Instead, learn:

> **Which command gives me which type of information?**

---

# 🧠 Knowledge Check

Try answering these without looking back first.

### 1. What is a computer network?

### 2. What is the difference between a client and a server?

### 3. What does a network interface allow a device to do?

### 4. What is the general purpose of an IP address?

### 5. What is the role of a default gateway?

### 6. What service helps translate names such as `github.com` into IP addresses?

### 7. Which Windows command displays basic IP configuration?

### 8. Which PowerShell command can display network adapter information?

### 9. What does a `169.254.x.x` address often suggest?

### 10. Why doesn't one successful `ping` prove that every part of the network is working?

---

# ✅ Knowledge Check Answers

### 1.

A network is a group of devices capable of communicating and sharing information or resources.

### 2.

A client requests a service or resource, while a server provides a service or resource.

### 3.

A network interface provides the connection a device uses to communicate on a network.

### 4.

An IP address identifies a host/interface within IP communication and helps traffic reach the appropriate destination.

### 5.

The default gateway provides a path toward destinations outside the device's local network.

### 6.

**DNS**

### 7.

```cmd
ipconfig
```

### 8.

```powershell
Get-NetAdapter
```

### 9.

The computer may have failed to obtain its expected IPv4 configuration through DHCP and assigned itself an APIPA address.

### 10.

Ping tests only a specific type of communication. Other services, protocols, name resolution, ports, or applications can still have problems.

---

# 📝 Key Takeaways

Before moving on, make sure you understand these ideas:

- A network allows devices to communicate.
- Clients request services.
- Servers provide services.
- Network interfaces connect devices to networks.
- IP addresses help identify network destinations.
- Default gateways help reach other networks.
- DNS helps resolve names.
- `ipconfig` displays Windows IP configuration.
- `Get-NetAdapter` displays network adapter information.
- `ping` is useful but doesn't prove everything is working.
- Troubleshooting should be based on evidence rather than random changes.

---

# 🎓 Network+ Exam Tip

Network+ questions often provide a **symptom** rather than asking only for a definition.

For example:

> A workstation can communicate with local systems but cannot reach remote networks.

One of the first things you might investigate is its:

**Default gateway**

Or:

> A workstation receives a `169.254.x.x` address.

A likely area to investigate is:

**DHCP / automatic address assignment**

As you progress through the course, try to connect every networking concept to a troubleshooting symptom.



---

# 🌐 Cisco Companion

Cisco Networking Academy material can provide additional practice with basic networking concepts.

➡️ [Cisco Networking Companion](../resources/cisco-companion.md)

Cisco activities are supplemental and do not need to be completed before continuing unless specifically marked as required in a lab.

---

# 🛠️ Project Progress

You're working toward:

➡️ **Project 01 — Build Your First Network**

Project 01 will be completed after Lessons 01–05.

For now, focus on understanding the foundational concepts.

---


# 🎥 Recommended Video

For an additional explanation of how devices communicate across a network:

### Professor Messer — Network Communication

**CompTIA Network+ N10-009 — Network Communication (3:55)**

➡️ [Watch — Network Communication](https://www.professormesser.com/network-plus/n10-009/n10-009-video/network-communication-n10-009/)

> ⭐ **Optional**
>
> This short Professor Messer video reinforces the basic network communication concepts introduced in this lesson and provides additional Network+ exam-focused context.
>
> You do not need to watch it before completing the lab.

---

---

# 🧪 Next Step — Complete the Lab

---

# 🧪 Hands-On Lab

Now put the lesson into practice.

➡️ **[Lab 01 — Networking Basics](../labs/lab-01-networking-basics.md)**

In the lab, you'll inspect your own Windows computer and identify:

- Network adapters
- IPv4 address
- Default gateway
- DNS servers
- Basic connectivity
- PowerShell network information

---

After completing Lab 01, continue to:

➡️ **[Lesson 02 — Network Types and Topologies](lesson-02-network-types-and-topologies.md)**
