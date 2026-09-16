# 🧰 Networking Command Reference

A practical command reference for the **Networking Fundamentals** course and **CompTIA Network+ N10-009** study.

This is not intended to replace understanding what the commands do.

Use it when you know:

> **What you want to check**

but can't remember:

> **Which command checks it.**

---

# 🪟 Windows Command Prompt

---

# 🌐 View Basic IP Configuration

```cmd
ipconfig
```

Displays basic network configuration.

Common information:

```text
IPv4 Address

Subnet Mask

Default Gateway
```

---

# 🌐 View Detailed IP Configuration

```cmd
ipconfig /all
```

Use this when troubleshooting.

Displays information such as:

```text
Hostname

DHCP Status

MAC Address

IPv4 Address

IPv6 Address

Subnet Mask

Default Gateway

DHCP Server

DNS Servers

Lease Information
```

### Troubleshooting Use

If a user says:

> "The network isn't working."

One of your first commands can be:

```cmd
ipconfig /all
```

Look for:

```text
Correct IP?

Correct subnet?

Correct gateway?

Correct DNS?

DHCP enabled?

169.254.x.x?
```

---

# 📦 Release DHCP Address

```cmd
ipconfig /release
```

Releases the current DHCP IPv4 lease.

Commonly followed by:

```cmd
ipconfig /renew
```

---

# 📦 Renew DHCP Address

```cmd
ipconfig /renew
```

Requests DHCP configuration.

Useful after:

```text
DHCP changes

VLAN corrections

Network reconnection

DHCP troubleshooting
```

---

# 📛 Display DNS Cache

```cmd
ipconfig /displaydns
```

Displays cached DNS information.

---

# 🧹 Clear DNS Cache

```cmd
ipconfig /flushdns
```

Clears the Windows DNS resolver cache.

Useful when:

```text
DNS record changed

Old address is cached

Name resolves incorrectly
```

---

# 📛 Register DNS

```cmd
ipconfig /registerdns
```

Initiates DNS registration for configured adapters.

More relevant in managed Windows environments using dynamic DNS.

---

# 🏓 PING

Basic syntax:

```cmd
ping <destination>
```

Example:

```cmd
ping 192.168.1.1
```

or:

```cmd
ping example.com
```

Tests basic IP reachability using ICMP echo where permitted.

---

# 🔁 Continuous Ping

```cmd
ping 8.8.8.8 -t
```

Continues until stopped.

Stop with:

```text
Ctrl + C
```

Useful for watching:

```text
Intermittent connectivity

Packet loss

Device reboot

Wi-Fi changes

Failover
```

---

# 🔢 Ping a Specific Number of Times

```cmd
ping 8.8.8.8 -n 10
```

Sends:

```text
10
```

echo requests.

---

# 📦 Ping with Larger Payload

```cmd
ping 8.8.8.8 -l 1400
```

Useful in some MTU-related investigations.

---

# 🚫 Don't Fragment

On Windows:

```cmd
ping 8.8.8.8 -f -l 1400
```

Can help investigate IPv4 MTU/fragmentation behavior.

Exact results depend on the path and whether ICMP is permitted.

---

# 🧠 Recommended Ping Sequence

Start local and move outward.

### 1. Loopback

```cmd
ping 127.0.0.1
```

Tests the local IPv4 TCP/IP stack.

### 2. Your Own Address

```cmd
ping <your-IP>
```

### 3. Default Gateway

```cmd
ping <gateway>
```

Example:

```cmd
ping 192.168.1.1
```

### 4. Remote IP

```cmd
ping 8.8.8.8
```

### 5. Hostname

```cmd
ping example.com
```

This helps isolate:

```text
Local TCP/IP

NIC / local configuration

LAN

Gateway

Routing

Internet

DNS
```

---

# 🗺️ TRACERT

```cmd
tracert <destination>
```

Example:

```cmd
tracert 8.8.8.8
```

Displays Layer 3 hops toward the destination where responses are available.

Useful for identifying:

```text
Where the path stops

Unexpected routing

WAN problems

High-delay portions of a path
```

---

# 🧭 PATHPING

```cmd
pathping <destination>
```

Example:

```cmd
pathping 8.8.8.8
```

Combines concepts from:

```text
ping
+
tracert
```

and gathers statistics over time.

Useful for investigating:

```text
Packet loss

Latency

Problematic path segments
```

Interpret results carefully because some routers rate-limit or ignore ICMP.

---

# 📛 NSLOOKUP

```cmd
nslookup <hostname>
```

Example:

```cmd
nslookup example.com
```

Queries DNS.

Useful when:

```text
IP works
but
hostname doesn't
```

---

# 📛 Query a Specific DNS Server

```cmd
nslookup example.com 8.8.8.8
```

This asks a specific DNS server.

Useful for comparing:

```text
Corporate DNS

Public DNS

Different DNS Servers
```

---

# 📛 Interactive NSLOOKUP

Start:

```cmd
nslookup
```

Then enter queries interactively.

Exit:

```text
exit
```

---

# 🔍 ARP TABLE

```cmd
arp -a
```

Displays the ARP cache.

Shows:

```text
IPv4 Address
↔
MAC Address
```

Useful for local Layer 2/Layer 3 troubleshooting.

---

# 🧹 Delete ARP Entry

Example:

```cmd
arp -d <IP-address>
```

Use carefully.

This removes a cached ARP mapping so it can be learned again.

---

# 🛣️ ROUTING TABLE

```cmd
route print
```

Displays the Windows routing table.

Look for:

```text
Default Route

Local Networks

Gateway

Interface

Metric
```

---

# 🔌 NETSTAT

Basic:

```cmd
netstat
```

Displays active network connections.

---

# 🔍 Numeric Addresses

```cmd
netstat -n
```

Avoids hostname/service-name resolution.

---

# 👀 Listening and Active Connections

```cmd
netstat -a
```

Displays active connections and listening ports.

---

# 🔢 Show Process IDs

```cmd
netstat -o
```

Shows the PID associated with connections.

---

# ⭐ Common Combination

```cmd
netstat -ano
```

Very useful for:

```text
Active connections

Listening ports

Remote addresses

Process IDs
```

---

# 🧾 Associate Connections with Executables

Run an elevated Command Prompt:

```cmd
netstat -b
```

This may take longer and requires appropriate permissions.

---

# 🖥️ HOSTNAME

```cmd
hostname
```

Displays the computer's hostname.

---

# 🔎 WHOAMI

```cmd
whoami
```

Displays the current user identity.

Useful when troubleshooting:

```text
Permissions

Authentication

Remote sessions
```

---

# 📋 GETMAC

```cmd
getmac
```

Displays MAC address information for network adapters.

---

# 🔌 IPCONFIG + GETMAC

For a quick comparison:

```cmd
ipconfig /all
```

and:

```cmd
getmac
```

can help identify adapters and their addresses.

---

# 📶 Windows Wi-Fi Commands

Display current wireless information:

```cmd
netsh wlan show interfaces
```

Useful information may include:

```text
SSID

Signal

Radio Type

Channel

Receive Rate

Transmit Rate
```

---

# 📶 Show Wireless Profiles

```cmd
netsh wlan show profiles
```

Displays saved wireless profiles.

---

# 📶 WLAN Driver Information

```cmd
netsh wlan show drivers
```

Useful for checking supported wireless capabilities.

---

# 💻 PowerShell Networking

Modern Windows includes useful networking cmdlets.

---

# 🔌 Network Adapters

```powershell
Get-NetAdapter
```

Displays adapters and status.

Look for:

```text
Name

Interface Description

Status

Link Speed

MAC Address
```

---

# 🌐 IP Configuration

```powershell
Get-NetIPConfiguration
```

PowerShell equivalent of viewing important IP configuration.

---

# 🌐 IP Addresses

```powershell
Get-NetIPAddress
```

Displays configured IP addresses.

Filter IPv4:

```powershell
Get-NetIPAddress -AddressFamily IPv4
```

---

# 🛣️ Routes

```powershell
Get-NetRoute
```

Displays the routing table.

IPv4 only:

```powershell
Get-NetRoute -AddressFamily IPv4
```

---

# 📛 DNS Servers

```powershell
Get-DnsClientServerAddress
```

Displays configured DNS servers.

---

# 📛 DNS Query

```powershell
Resolve-DnsName example.com
```

Useful alternative to:

```cmd
nslookup
```

---

# 🧪 Test Network Connection

```powershell
Test-NetConnection example.com
```

Can provide:

```text
Name Resolution

Remote Address

Ping Result
```

depending on the target and network policy.

---

# 🔌 Test TCP Port

```powershell
Test-NetConnection example.com -Port 443
```

Very useful.

Example:

```powershell
Test-NetConnection server01 -Port 445
```

This helps answer:

> Can I reach this specific TCP service?

---

# 🛣️ Trace Route with PowerShell

```powershell
Test-NetConnection example.com -TraceRoute
```

---

# 🔍 View TCP Connections

```powershell
Get-NetTCPConnection
```

Useful for examining:

```text
Local Address

Local Port

Remote Address

Remote Port

Connection State
```

---

# 🔥 Windows Firewall Profiles

```powershell
Get-NetFirewallProfile
```

Displays firewall profile status.

---

# 🔥 Firewall Rules

```powershell
Get-NetFirewallRule
```

Can return a large amount of information.

Filtering is usually helpful in real administration.

---

# 🔀 CISCO IOS — BASIC NAVIGATION

Enter privileged EXEC mode:

```text
enable
```

Enter global configuration:

```text
configure terminal
```

Shortcut:

```text
conf t
```

Exit current configuration level:

```text
exit
```

Return to privileged EXEC:

```text
end
```

---

# 🔍 Cisco Interface Summary

```text
show ip interface brief
```

One of the most useful Cisco troubleshooting commands.

Shows:

```text
Interface

IP Address

Status

Protocol
```

---

# 🔌 Detailed Interfaces

```text
show interfaces
```

Useful for checking:

```text
Status

Errors

Traffic

Duplex

Speed

Drops
```

---

# 🔌 Specific Interface

Example:

```text
show interfaces gigabitEthernet0/1
```

Actual interface names vary by device.

---

# 🧱 VLANs

```text
show vlan brief
```

Displays:

```text
VLAN ID

VLAN Name

Status

Access Ports
```

---

# 🌉 Trunks

```text
show interfaces trunk
```

Useful for verifying:

```text
Trunk Status

Native VLAN

Allowed VLANs

Active VLANs
```

---

# 📬 MAC Address Table

```text
show mac address-table
```

Displays:

```text
MAC Address

VLAN

Switch Port
```

---

# 🛣️ Routing Table

```text
show ip route
```

Displays routes known by the router.

Look for:

```text
Connected Routes

Static Routes

Default Route

Dynamically Learned Routes
```

---

# 📋 Current Configuration

```text
show running-config
```

Displays the configuration currently active in memory.

---

# 💾 Saved Configuration

```text
show startup-config
```

Displays the configuration intended for startup.

---

# 💾 Save Configuration

```text
copy running-config startup-config
```

Common shorthand:

```text
write memory
```

or:

```text
wr
```

depending on platform/support.

---

# 🏷️ Set Hostname

```text
configure terminal

hostname SW-01
```

---

# 🧱 Create VLAN

```text
configure terminal

vlan 10
 name EMPLOYEES

exit
```

Verify:

```text
show vlan brief
```

---

# 🔌 Configure Access Port

Example:

```text
configure terminal

interface fa0/1

switchport mode access

switchport access vlan 10

no shutdown

end
```

---

# 🌉 Configure Trunk

Example:

```text
configure terminal

interface g0/1

switchport mode trunk

no shutdown

end
```

Verify:

```text
show interfaces trunk
```

---

# 🚫 Disable Interface

```text
configure terminal

interface fa0/10

shutdown

end
```

---

# 🟢 Enable Interface

```text
configure terminal

interface fa0/10

no shutdown

end
```

---

# 🔒 Disable Multiple Unused Ports

Example:

```text
configure terminal

interface range fa0/10-24

shutdown

end
```

Be absolutely certain the ports are unused before doing this on a real network.

---

# 🌐 Configure Router Interface

Example:

```text
configure terminal

interface g0/0

ip address 192.168.1.1 255.255.255.0

no shutdown

end
```

---

# 🛣️ Static Route

Syntax:

```text
ip route <destination-network> <mask> <next-hop>
```

Example:

```text
ip route 192.168.20.0 255.255.255.0 10.0.0.2
```

---

# 🌎 Default Route

```text
ip route 0.0.0.0 0.0.0.0 <next-hop>
```

Example:

```text
ip route 0.0.0.0 0.0.0.0 10.0.0.2
```

---

# 🏷️ Router-on-a-Stick

Physical interface:

```text
interface g0/0

no shutdown
```

Subinterface:

```text
interface g0/0.10

encapsulation dot1Q 10

ip address 192.168.10.1 255.255.255.0
```

Another VLAN:

```text
interface g0/0.20

encapsulation dot1Q 20

ip address 192.168.20.1 255.255.255.0
```

---

# 📦 Cisco DHCP — Excluded Addresses

Example:

```text
ip dhcp excluded-address 192.168.10.1 192.168.10.20
```

Prevents those addresses from being dynamically assigned by the router's DHCP service.

---

# 📦 Cisco DHCP Pool

Example:

```text
ip dhcp pool EMPLOYEES

network 192.168.10.0 255.255.255.0

default-router 192.168.10.1

dns-server 192.168.20.10
```

---

# 📋 View DHCP Configuration

Useful commands can include:

```text
show running-config
```

and, depending on IOS/device support:

```text
show ip dhcp binding
```

---

# 🏓 Cisco Ping

```text
ping 192.168.10.1
```

Useful for testing connectivity directly from a network device.

---

# 🗺️ Cisco Traceroute

```text
traceroute 8.8.8.8
```

Cisco uses:

```text
traceroute
```

while Windows commonly uses:

```text
tracert
```

---

# 🔐 Basic SSH Concepts

Typical Cisco SSH configuration involves:

```text
Hostname

Domain Name

RSA Keys

Local User

VTY Configuration

SSH Transport
```

Example training configuration:

```text
hostname SW-01

ip domain-name northstar.local

username admin privilege 15 secret <password>

crypto key generate rsa
```

Then:

```text
line vty 0 4

login local

transport input ssh
```

Exact syntax and supported features can vary by IOS/device.

---

# 📋 ACL Commands

Create a named extended ACL:

```text
ip access-list extended GUEST_FILTER
```

Example deny:

```text
deny ip 192.168.50.0 0.0.0.255 192.168.20.0 0.0.0.255
```

Example permit:

```text
permit ip 192.168.50.0 0.0.0.255 any
```

Apply to an interface:

```text
interface g0/0.50

ip access-group GUEST_FILTER in
```

---

# 🔍 View ACLs

```text
show access-lists
```

or:

```text
show ip access-lists
```

depending on device/platform.

---

# 🧮 Wildcard Masks

Cisco ACLs commonly use wildcard masks.

Example subnet:

```text
192.168.10.0/24
```

Subnet mask:

```text
255.255.255.0
```

Wildcard:

```text
0.0.0.255
```

Easy relationship:

```text
255.255.255.255
-
Subnet Mask
=
Wildcard Mask
```

---

# 📊 Cisco Troubleshooting Set

If you're not sure where to begin:

```text
show ip interface brief
```

```text
show interfaces
```

```text
show vlan brief
```

```text
show interfaces trunk
```

```text
show mac address-table
```

```text
show ip route
```

```text
show running-config
```

```text
show access-lists
```

Then test:

```text
ping
```

and:

```text
traceroute
```

---

# 🧪 DNS TROUBLESHOOTING COMMAND SET

Windows:

```cmd
ipconfig /all
```

Check configured DNS servers.

Then:

```cmd
nslookup example.com
```

Or PowerShell:

```powershell
Resolve-DnsName example.com
```

Compare IP connectivity:

```cmd
ping 8.8.8.8
```

against hostname:

```cmd
ping example.com
```

If:

```text
IP
✓

Hostname
X
```

investigate DNS.

---

# 📦 DHCP TROUBLESHOOTING COMMAND SET

Start:

```cmd
ipconfig /all
```

Look for:

```text
169.254.x.x

Wrong subnet

Wrong gateway

Wrong DNS

Unexpected DHCP server
```

Then:

```cmd
ipconfig /release
```

```cmd
ipconfig /renew
```

If DHCP still fails, investigate:

```text
Physical Connection

Wi-Fi

Switch Port

VLAN

DHCP Scope

DHCP Server

DHCP Relay
```

---

# 📶 WI-FI TROUBLESHOOTING COMMAND SET

```cmd
netsh wlan show interfaces
```

Check:

```text
SSID

Signal

Radio Type

Channel

Receive Rate

Transmit Rate
```

Then:

```cmd
ipconfig /all
```

Check:

```text
IP

Gateway

DNS

DHCP
```

Then test:

```cmd
ping <gateway>
```

---

# 🛣️ ROUTING TROUBLESHOOTING COMMAND SET

Windows:

```cmd
ipconfig /all
```

```cmd
route print
```

```cmd
ping <gateway>
```

```cmd
tracert <destination>
```

Cisco:

```text
show ip interface brief
```

```text
show ip route
```

```text
ping <destination>
```

```text
traceroute <destination>
```

---

# 🔀 VLAN TROUBLESHOOTING COMMAND SET

Cisco:

```text
show vlan brief
```

```text
show interfaces trunk
```

```text
show mac address-table
```

```text
show running-config
```

Check:

```text
Correct VLAN exists?

Correct access port?

Correct trunk?

VLAN allowed across trunk?

Router/L3 interface available?
```

---

# 🔥 SERVICE TROUBLESHOOTING

A device responding to ping does not prove an application works.

Example:

```powershell
Test-NetConnection server01 -Port 443
```

This tests:

> **TCP 443**

instead of only testing IP reachability.

Another example:

```powershell
Test-NetConnection server01 -Port 445
```

tests SMB connectivity.

---

# ⭐ QUICK COMMAND MAP

| Need to Check | Command |
|---|---|
| Windows IP config | `ipconfig /all` |
| DHCP renew | `ipconfig /renew` |
| Clear DNS cache | `ipconfig /flushdns` |
| Reachability | `ping` |
| Network path | `tracert` |
| Path/loss | `pathping` |
| DNS | `nslookup` |
| ARP | `arp -a` |
| Windows routes | `route print` |
| Connections/ports | `netstat -ano` |
| Wi-Fi status | `netsh wlan show interfaces` |
| PowerShell adapters | `Get-NetAdapter` |
| PowerShell IP config | `Get-NetIPConfiguration` |
| PowerShell routes | `Get-NetRoute` |
| DNS lookup | `Resolve-DnsName` |
| Test TCP port | `Test-NetConnection` |
| Cisco interfaces | `show ip interface brief` |
| Cisco VLANs | `show vlan brief` |
| Cisco trunks | `show interfaces trunk` |
| Cisco MAC table | `show mac address-table` |
| Cisco routes | `show ip route` |
| Cisco configuration | `show running-config` |
| Cisco ACLs | `show access-lists` |

---

# 🧠 Troubleshooting Mental Model

Commands are tools.

The real skill is knowing:

> **Which question you're trying to answer.**

Example:

```text
Does the PC have an IP?
        ↓
ipconfig /all
```

```text
Can I reach the gateway?
        ↓
ping
```

```text
Where does the path stop?
        ↓
tracert
```

```text
Does DNS work?
        ↓
nslookup
```

```text
Can I reach TCP 443?
        ↓
Test-NetConnection
```

```text
Is the PC in the correct VLAN?
        ↓
show vlan brief
```

```text
Are VLANs crossing the uplink?
        ↓
show interfaces trunk
```

```text
Does the router know the destination?
        ↓
show ip route
```

```text
What changed in the configuration?
        ↓
show running-config
```

The command itself isn't the troubleshooting method.

> **The command provides evidence.**

---

# 🏆 Five Commands to Remember First

If you're just starting, remember these Windows commands:

```text
ipconfig /all

ping

tracert

nslookup

arp -a
```

And these Cisco commands:

```text
show ip interface brief

show vlan brief

show interfaces trunk

show mac address-table

show ip route
```

Once those become familiar, the rest are much easier to add.

---

# 📚 Course Navigation

➡️ **[Cheat Sheet](cheat-sheet.md)**

➡️ **[Exam Tips](exam-tips.md)**

➡️ **[Glossary](glossary.md)**

➡️ **[Return to Main README](../README.md)**

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**