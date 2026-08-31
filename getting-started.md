[🚀 Getting Started — Networking Fundamentals.md](https://github.com/user-attachments/files/31656927/Getting.Started.Networking.Fundamentals.md)
# 🚀 Getting Started — Networking Fundamentals

Welcome to **Networking Fundamentals**!

Before beginning Lesson 01, take a few minutes to prepare your computer and become familiar with the tools we'll use throughout the course.

Don't worry if you've never used some of these tools before.

You are **not expected to know how they work yet** — that's what the lessons and labs are for.

---

# 🎯 Before You Begin

For the best experience, you should have:

- A Windows computer
- Administrator access to install software
- Internet access
- A web browser
- A free Cisco account
- Cisco Packet Tracer
- Wireshark
- Windows PowerShell
- Windows Command Prompt
- A GitHub account — optional, but useful

Most of the tools used in this course are **free**.

---

# 🧰 Tools We'll Use

| Tool | Purpose | Required? |
|---|---|---|
| 🖥️ Windows | Networking commands and administration | ✅ Yes |
| 🌐 Cisco Packet Tracer | Build and simulate networks | ✅ Yes |
| 🦈 Wireshark | Capture and analyze network traffic | ✅ Yes |
| 🔷 PowerShell | Network investigation and administration | ✅ Yes |
| ⌨️ Command Prompt | Traditional Windows networking commands | ✅ Yes |
| 🎓 Cisco Networking Academy / Skills for All | Supplemental training and exercises | ⭐ Recommended |
| 🐙 GitHub | Store notes and follow the training repository | Optional |

You don't need to master any of these before starting.

We'll introduce them as we need them.

---

# 🌐 1. Cisco Networking Academy / Skills for All

Cisco provides free networking training through **Cisco Networking Academy / Skills for All**.

We'll use selected Cisco material as a companion to this course.

Cisco provides additional:

- Interactive networking lessons
- Network simulations
- Packet Tracer activities
- Knowledge checks
- Networking exercises
- Cisco-focused configuration practice

Create a free Cisco account if you don't already have one.

➡️ **Cisco Skills for All:**  
https://skillsforall.com/

---

## 📘 Cisco Networking Basics

One of the primary companion resources for this course is Cisco's **Networking Basics** training.

You do **not** need to complete the entire Cisco course before beginning this one.

Instead, we'll point you toward relevant Cisco sections as you progress through the lessons.

Think of it as:

**Networking Fundamentals → Hands-On Lab → Cisco Practice → Continue Learning**

Our Cisco mappings are available here:

➡️ [Cisco Networking Companion](resources/cisco-companion.md)

---

# 🌐 2. Cisco Packet Tracer

**Cisco Packet Tracer** allows you to build virtual computer networks without needing physical switches, routers, servers, or dozens of computers.

You'll be able to create networks containing devices such as:

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
Other Networks
```

Later, you'll build much larger environments.

---

## 🧪 What We'll Use Packet Tracer For

Throughout the course, Packet Tracer may be used to:

- Connect computers
- Configure switches
- Configure routers
- Assign IP addresses
- Configure default gateways
- Configure DHCP
- Configure DNS
- Build LANs
- Connect multiple networks
- Test network connectivity
- Observe network traffic
- Troubleshoot broken networks

This lets you experiment without risking a real production network.

---

## 📥 Download Packet Tracer

Cisco provides Packet Tracer through its Skills for All resources.

➡️ **Packet Tracer Downloads:**  
https://skillsforall.com/resources/lab-downloads

You may need to sign into your Cisco account before downloading.

Packet Tracer is available for supported desktop operating systems including Windows, Linux, and macOS.

---

## ✅ Test Packet Tracer

After installation:

1. Open **Cisco Packet Tracer**.
2. Sign in with your Cisco account if prompted.
3. Confirm that the main Packet Tracer workspace opens.
4. Locate the device categories near the bottom of the application.

You don't need to build anything yet.

If Packet Tracer opens successfully, you're ready.

---

# 🦈 3. Wireshark

**Wireshark** is a network protocol analyzer.

It allows you to capture and inspect network traffic traveling through your computer.

Instead of simply seeing:

> "The website loaded."

Wireshark lets you begin investigating **what actually happened on the network**.

You'll eventually be able to examine protocols such as:

- ARP
- DNS
- DHCP
- ICMP
- TCP
- UDP
- HTTP
- TLS

Wireshark will become especially useful once we begin learning how protocols communicate.

---

## 📥 Download Wireshark

Download Wireshark from the official Wireshark website:

➡️ **Wireshark Download:**  
https://www.wireshark.org/download.html

For most Windows computers, use the current **stable Windows x64 installer**.

During installation, you may also be prompted to install **Npcap**.

Npcap allows Wireshark to capture network packets on Windows and should normally be installed.

---

## ⚠️ A Note About Packet Captures

Only capture or inspect network traffic on systems and networks you are authorized to use.

Throughout this course, we'll primarily analyze traffic generated by:

- Your own computer
- Your own lab environment
- Packet Tracer
- Purpose-built training exercises

---

## ✅ Test Wireshark

After installation:

1. Open **Wireshark**.
2. Confirm that network interfaces appear.
3. Look for interfaces such as:

```text
Ethernet
Wi-Fi
```

You don't need to capture anything yet.

If Wireshark opens and displays network interfaces, you're ready.

---

# 🔷 4. Windows PowerShell

PowerShell is already included with modern Windows environments and provides powerful networking commands.

To open PowerShell:

1. Open **Start**.
2. Search for:

```text
PowerShell
```

3. Open **Windows PowerShell** or your installed version of **PowerShell**.

---

## 🧪 Test PowerShell

Run:

```powershell
Get-NetAdapter
```

You should see information about your computer's network adapters.

You may see adapters such as:

```text
Ethernet
Wi-Fi
Bluetooth Network Connection
VPN adapters
Virtual adapters
```

Don't worry about understanding all of the output yet.

---

# ⌨️ 5. Windows Command Prompt

Many classic networking commands are commonly run from **Command Prompt**.

To open it:

1. Open **Start**.
2. Search for:

```text
cmd
```

3. Open **Command Prompt**.

---

## 🧪 Test Command Prompt

Run:

```cmd
ipconfig
```

You should see information about your computer's network configuration.

You may notice terms such as:

```text
IPv4 Address
Subnet Mask
Default Gateway
DNS
```

If those terms don't mean much yet, that's completely fine.

We'll learn what they mean later.

---

# 🔍 6. Networking Commands You'll Learn

Throughout the course, you'll gradually become comfortable with commands such as:

## Command Prompt

```cmd
ipconfig
ipconfig /all
ping
tracert
nslookup
arp -a
netstat
route print
```

## PowerShell

```powershell
Get-NetAdapter
Get-NetIPConfiguration
Get-NetIPAddress
Get-DnsClientServerAddress
Resolve-DnsName
Test-NetConnection
Get-NetRoute
```

You are **not expected to memorize these now**.

The labs will teach you when each command is useful.

---

# 🐙 7. GitHub

GitHub isn't required for learning networking, but it's useful for following this course and building your own technical documentation.

You can create a free GitHub account here:

➡️ **GitHub:**  
https://github.com/

You may want to use GitHub to store:

- Networking notes
- Lab results
- Troubleshooting notes
- Network diagrams
- Command references
- Practice projects

Building your own documentation while learning can become a useful reference later.

---

# 📝 8. Optional — A Notes System

Networking introduces a lot of terminology.

Consider keeping notes somewhere convenient.

You could use:

- Markdown files
- OneNote
- Notepad
- VS Code
- GitHub
- Word
- A physical notebook

Don't try to write down everything.

Focus on things such as:

```text
What does this technology do?

Why is it needed?

Where would I see it?

How would I troubleshoot it?

What command could help me investigate it?
```

Those questions are much more valuable than memorizing definitions alone.

---

# 🧠 Recommended Learning Approach

For each topic, try to follow this pattern:

```text
1. Learn the concept
        ↓
2. See an example
        ↓
3. Use the technology
        ↓
4. Observe what happens
        ↓
5. Break something
        ↓
6. Troubleshoot it
        ↓
7. Explain why it worked
```

That final step is important.

If you can explain **why something worked**, you're beginning to understand networking rather than simply following instructions.

---

# 🛡️ Lab Safety

Some networking tools can interact with real networks.

Throughout this course:

- Don't change production network equipment without authorization.
- Don't scan networks you don't own or have permission to test.
- Don't capture other people's network traffic.
- Don't change corporate firewall, switch, router, or DHCP settings for practice.
- Use Packet Tracer or a dedicated lab environment when configuration changes are required.

The goal is to learn networking **without disrupting a real environment**.

---

# ✅ Pre-Course Checklist

Before moving to Lesson 01, verify the following:

- [ ] I have access to a Windows computer.
- [ ] I can open Command Prompt.
- [ ] I can run `ipconfig`.
- [ ] I can open PowerShell.
- [ ] I can run `Get-NetAdapter`.
- [ ] I created or have access to a Cisco account.
- [ ] Cisco Packet Tracer is installed.
- [ ] Packet Tracer opens successfully.
- [ ] Wireshark is installed.
- [ ] Wireshark opens and detects my network interfaces.
- [ ] I understand that Cisco training will be used as supplemental practice.
- [ ] I'm ready to start learning networking.

If you checked everything above, your networking lab environment is ready.

---

# 🆘 Don't Have Everything Installed Yet?

That's okay.

Not every tool will be used immediately.

The early lessons focus heavily on understanding networking concepts before moving into more advanced configuration and packet analysis.

The two most important things at the beginning are:

**A computer you can practice on + curiosity about how networks work.**

The rest we'll build as we go.

---

# ➡️ Next Step

Your environment is ready.

Continue to:

➡️ **[Networking Lessons](lessons/README.md)**

Then begin:

➡️ **Lesson 01 — Networking Basics**
