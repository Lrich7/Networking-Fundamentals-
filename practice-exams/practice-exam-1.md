# 📝 Networking Fundamentals — Practice Exam 1

**Lessons Covered:** 1–10  
**Questions:** 40  
**Recommended Time:** 50 minutes

This practice exam reviews the first half of the Networking Fundamentals course and reinforces concepts commonly encountered on the **CompTIA Network+ N10-009** exam.

---

# 📋 Instructions

- Choose the **BEST** answer for each question.
- Do not use the answer key until you finish.
- Use scratch paper for subnetting questions.
- Pay attention to words such as **FIRST**, **BEST**, and **MOST LIKELY**.
- For troubleshooting questions, use the symptoms provided rather than assuming additional problems.

Recommended goal:

```text
36–40 = Excellent
32–35 = Strong
28–31 = Review weak areas
Below 28 = Review Lessons 1–10 before continuing
```

> The score ranges above are study targets for this course, not official CompTIA passing-score conversions.

---

# Question 1

Which device primarily forwards Ethernet frames based on MAC addresses?

A. Router  
B. Switch  
C. Firewall  
D. DNS server

---

# Question 2

Which device is primarily responsible for forwarding packets between different IP networks?

A. Switch  
B. Access point  
C. Router  
D. Patch panel

---

# Question 3

Which type of network generally covers a relatively small geographic area such as an office or building?

A. WAN  
B. LAN  
C. MAN  
D. PAN

---

# Question 4

Which type of network connects geographically separated locations?

A. LAN  
B. VLAN  
C. WAN  
D. PAN

---

# Question 5

Which OSI layer is responsible for IP addressing and routing?

A. Layer 1  
B. Layer 2  
C. Layer 3  
D. Layer 4

---

# Question 6

Which OSI layer is most closely associated with MAC addresses and Ethernet frames?

A. Physical  
B. Data Link  
C. Network  
D. Transport

---

# Question 7

Which OSI layer is associated with TCP and UDP?

A. Layer 2  
B. Layer 3  
C. Layer 4  
D. Layer 7

---

# Question 8

Which protocol provides reliable, connection-oriented transport?

A. UDP  
B. TCP  
C. ICMP  
D. ARP

---

# Question 9

Which characteristic best describes UDP?

A. Requires a three-way handshake  
B. Guarantees ordered delivery  
C. Connectionless with relatively low overhead  
D. Automatically retransmits all lost packets

---

# Question 10

What is the primary purpose of ARP in IPv4 Ethernet networks?

A. Resolve a hostname to an IP address  
B. Resolve an IPv4 address to a MAC address  
C. Assign an IP address automatically  
D. Determine the Internet route to a server

---

# Question 11

A workstation has the following address:

```text
169.254.25.17
```

What does this MOST likely indicate?

A. The workstation successfully received DHCP configuration  
B. The workstation is using a public Internet address  
C. The workstation did not obtain normal IPv4 configuration from DHCP  
D. The workstation is configured as a DNS server

---

# Question 12

Which protocol automatically provides clients with information such as an IP address, subnet mask, default gateway, and DNS server?

A. DNS  
B. DHCP  
C. ARP  
D. SNMP

---

# Question 13

What is the correct order of the DHCP DORA process?

A. Discover, Request, Offer, Acknowledge  
B. Discover, Offer, Request, Acknowledge  
C. Request, Discover, Acknowledge, Offer  
D. Offer, Discover, Request, Acknowledge

---

# Question 14

Which service translates names such as:

```text
server01.example.local
```

into IP addresses?

A. DHCP  
B. DNS  
C. ARP  
D. NTP

---

# Question 15

A user can successfully ping:

```text
8.8.8.8
```

but cannot access websites by hostname.

Which service should be investigated FIRST?

A. DHCP  
B. DNS  
C. NTP  
D. SNMP

---

# Question 16

What is the purpose of a default gateway?

A. Assign MAC addresses  
B. Provide DNS resolution  
C. Forward traffic destined for remote networks  
D. Automatically assign IP addresses

---

# Question 17

A PC has:

```text
IP Address:
192.168.10.25

Subnet Mask:
255.255.255.0

Default Gateway:
192.168.10.1
```

The PC needs to communicate with:

```text
192.168.20.50
```

Where will the PC send the packet toward FIRST?

A. DNS server  
B. DHCP server  
C. Default gateway  
D. Broadcast address

---

# Question 18

Which of the following is a private IPv4 address?

A. 8.8.8.8  
B. 172.20.10.5  
C. 169.254.1.5  
D. 1.1.1.1

---

# Question 19

Which range is part of the RFC1918 private IPv4 address space?

A. 172.16.0.0 through 172.31.255.255  
B. 172.0.0.0 through 172.255.255.255  
C. 169.254.0.0 through 169.254.255.255  
D. 127.0.0.0 through 127.255.255.255

---

# Question 20

Which IPv4 address is commonly used to test the local TCP/IP stack?

A. 0.0.0.0  
B. 127.0.0.1  
C. 169.254.0.1  
D. 255.255.255.255

---

# Question 21

What subnet mask corresponds to:

```text
/24
```

A. 255.255.0.0  
B. 255.255.255.0  
C. 255.255.255.128  
D. 255.255.255.192

---

# Question 22

How many traditional usable host addresses are available in a `/26` IPv4 subnet?

A. 30  
B. 62  
C. 64  
D. 126

---

# Question 23

What is the subnet mask for:

```text
/27
```

A. 255.255.255.192  
B. 255.255.255.224  
C. 255.255.255.240  
D. 255.255.255.248

---

# Question 24

What is the network address for:

```text
192.168.1.70/27
```

A. 192.168.1.0  
B. 192.168.1.32  
C. 192.168.1.64  
D. 192.168.1.70

---

# Question 25

What is the broadcast address for:

```text
192.168.1.70/27
```

A. 192.168.1.79  
B. 192.168.1.94  
C. 192.168.1.95  
D. 192.168.1.96

---

# Question 26

You need an IPv4 subnet that supports **25 traditional usable host addresses**.

Which is the smallest suitable subnet?

A. /28  
B. /27  
C. /26  
D. /25

---

# Question 27

Two computers have these addresses:

```text
PC-A
192.168.10.20/25

PC-B
192.168.10.200/25
```

Which statement is correct?

A. They are on the same subnet  
B. They are on different subnets  
C. They have duplicate addresses  
D. Both addresses are broadcast addresses

---

# Question 28

What is the traditional usable host range for:

```text
10.0.0.16/29
```

A. 10.0.0.16–10.0.0.23  
B. 10.0.0.17–10.0.0.22  
C. 10.0.0.17–10.0.0.23  
D. 10.0.0.18–10.0.0.22

---

# Question 29

What is the primary purpose of a VLAN?

A. Increase Internet bandwidth  
B. Create logical Layer 2 network segmentation  
C. Replace routing  
D. Automatically assign IP addresses

---

# Question 30

Devices in VLAN 10 need to communicate with devices in VLAN 20.

What is required?

A. Layer 3 routing  
B. DNS recursion  
C. ARP between the VLANs only  
D. A larger subnet mask on every device

---

# Question 31

Which switch port type normally carries traffic for multiple VLANs between network devices?

A. Access port  
B. Console port  
C. Trunk port  
D. Routed host port

---

# Question 32

Which standard is commonly associated with VLAN tagging on Ethernet trunks?

A. 802.1Q  
B. 802.11ax  
C. 802.3af  
D. 802.1X

---

# Question 33

Which Cisco command is MOST useful for quickly viewing VLANs and their assigned access ports?

A. `show ip route`  
B. `show vlan brief`  
C. `show arp`  
D. `show interfaces trunk`

---

# Question 34

Which Cisco command is MOST useful for verifying trunk interfaces?

A. `show interfaces trunk`  
B. `show vlan brief`  
C. `show ip route`  
D. `show running-config interface`

---

# Question 35

Which technology allows devices such as wireless access points and IP phones to receive electrical power through Ethernet cabling?

A. NAT  
B. PoE  
C. VLAN  
D. STP

---

# Question 36

A user reports that their desktop suddenly lost network connectivity.

You discover:

```text
Ethernet link light:
OFF

Other users:
Working normally
```

What should you check FIRST?

A. DNS server records  
B. Ethernet cable and physical connection  
C. Organization-wide routing protocols  
D. Internet provider BGP configuration

---

# Question 37

A user reports intermittent network problems.

You run:

```text
ping 192.168.1.1 -t
```

What is the primary reason for using `-t` on Windows?

A. Test DNS continuously  
B. Send continuous echo requests until stopped  
C. Trace every router in the path  
D. Display the routing table

---

# Question 38

Which Windows command is BEST for displaying detailed IP configuration, including DHCP and DNS information?

A. `ping`  
B. `tracert`  
C. `ipconfig /all`  
D. `arp -a`

---

# Question 39

Which Windows command is BEST for determining the Layer 3 path toward a remote destination?

A. `tracert`  
B. `nslookup`  
C. `ipconfig`  
D. `getmac`

---

# Question 40

A technician is troubleshooting a workstation.

The workstation can:

```text
Ping 127.0.0.1
✓

Ping its own IP
✓

Ping the default gateway
✓

Ping 8.8.8.8
✓

Resolve example.com
X
```

What is the MOST likely problem?

A. Failed NIC  
B. Bad Ethernet cable  
C. DNS problem  
D. Incorrect default gateway

---

# 🏁 End of Practice Exam 1

Stop here before opening the answer key.

Record your answers:

```text
1.  _____
2.  _____
3.  _____
4.  _____
5.  _____
6.  _____
7.  _____
8.  _____
9.  _____
10. _____

11. _____
12. _____
13. _____
14. _____
15. _____
16. _____
17. _____
18. _____
19. _____
20. _____

21. _____
22. _____
23. _____
24. _____
25. _____
26. _____
27. _____
28. _____
29. _____
30. _____

31. _____
32. _____
33. _____
34. _____
35. _____
36. _____
37. _____
38. _____
39. _____
40. _____
```

---

# 📚 Course Navigation

➡️ **[Practice Exam 1 Answer Key](answer-key-practice-exam-1.md)**

➡️ **[Cheat Sheet](../CheatSheet/cheat-sheet.md)**

➡️ **[Subnetting Reference](../CheatSheet/subnetting-reference.md)**

➡️ **[Command Reference](../CheatSheet/command-reference.md)**

➡️ **[Lessons](../lessons/README.md)**

➡️ **[Labs](../labs/README.md)**

➡️ **[Return to Main README](../README.md)**