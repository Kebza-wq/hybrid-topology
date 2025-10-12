# hybrid-topology
Hybrid Topology Project with VLANs, IPv4, IPv6, DHCP, OSPF, and basic router security.

# 🌐 Hybrid Topology Network Configuration (IPv4 + IPv6 + VLANs + Security)

## 📘 Overview
This project implements a **Hybrid Network Topology** in **Cisco Packet Tracer** that integrates multiple routers (R1–R5), switches (S1–S5), servers, and PCs.  
It supports **IPv4**, **IPv6**, **VLAN segmentation**, **DHCP**, **DHCPv6 server**, and **OSPF/OSPFv3 routing** — with **basic router security** configured on all routers.

The design represents a scalable, multi-site network with interconnectivity between routers using serial links and VLANs for LAN separation at each site.

---

## 🧩 Network Design Summary

### 🔸 Topology Type
Hybrid (combination of bus, star, and partial mesh)

### 🔸 Devices
- **5 Routers (R1–R5)**- R1–R5 connected via serial links
- **5 Switches (S1–S5)** -S1–S5 (each router connected to one switch)
- **9 PCs**-PCs (VLAN 10)  
- **3 Servers**-Servers (VLAN 20)

### 🔸 VLANs
Each switch has two VLANs:
- **VLAN 10:** PCs (dynamic IPv4 via DHCP and diynamiv IPv6 via DHCPv6 server)
- **VLAN 20:** Servers (dynamic addressing)

### 🔸 Routing Protocols
- **OSPFv2** for IPv4
- **OSPFv3** for IPv6

### 🔸 Addressing
-IPv4 and IPv6
**Dynamic Configuration:** DHCPv4 and DHCPv6 enabled on all routers  

### 🔸 Addressing Overview

| Device | Function | IPv4 Network | IPv6 Network | VLAN | Address Type |
|---------|------------|---------------|---------------|-------|----------------|
| **R1** | Router | 192.168.1.1/24 | 2001:db8:1::1/64 | VLAN10 | Gateway |
| **R1 (Server VLAN)** |  | 192.168.11.1/24 | 2001:db8:1:10::1/64 | VLAN20 | Gateway |
| **R2** | Router | 192.168.2.1/24 | 2001:db8:2::1/64 | VLAN10 | Gateway |
| **R2 (Server VLAN)** |  | 192.168.12.1/24 | 2001:db8:2:10::1/64 | VLAN20 | Gateway |
| **R3** | Router | 192.168.3.1/24 | 2001:db8:3::1/64 | VLAN10 | Gateway |
| **R3 (Server VLAN)** |  | 192.168.13.1/24 | 2001:db8:3:10::1/64 | VLAN20 | Gateway |
| **R4** | Router | 192.168.4.1/24 | 2001:db8:4::1/64 | VLAN10 | Gateway |
| **R4 (Server VLAN)** |  | 192.168.14.1/24 | 2001:db8:4:10::1/64 | VLAN20 | Gateway |
| **R5** | Router | 192.168.5.1/24 | 2001:db8:5::1/64 | VLAN10 | Gateway |
| **R5 (Server VLAN)** |  | 192.168.15.1/24 | 2001:db8:5:10::1/64 | VLAN20 | Gateway |
| **PC1 (S1)** | End Device | DHCP | DHCPv6 | VLAN10 | Dynamic |
| **Server1 (S1)** | DNS/HTTP | 192.168.11.10 | 2001:db8:1:10::10 | VLAN20 | dynamic |
| **PC2 (S2)** | End Device | DHCP | DHCPv6 | VLAN10 | Dynamic |
| **Server2 (S2)** | DNS/HTTP | 192.168.12.10 | 2001:db8:2:10::10 | VLAN20 | dynamic |
| **PC3 (S3)** | End Device | DHCP | DHCPv6 | VLAN10 | Dynamic |
| **Server3 (S3)** | DNS/HTTP | 192.168.13.10 | 2001:db8:3:10::10 | VLAN20 | dynamic |
| **PC4 (S4)** | End Device | DHCP | DHCPv6 | VLAN10 | Dynamic |
| **Server4 (S4)** | DNS/HTTP | 192.168.14.10 | 2001:db8:4:10::10 | VLAN20 | dynamic |
| **PC5 (S5)** | End Device | DHCP | DHCPv6 | VLAN10 | Dynamic |
| **Server5 (S5)** | DNS/HTTP | 192.168.15.10 | 2001:db8:5:10::10 | VLAN20 | dynamic |

### 🔸 Serial Link IP Plan
| Link | IPv4 | IPv6 |
|------|------|------|
| R1–R2 | 10.0.12.0/30 | 2001:db8:10:12::/64 |
| R2–R3 | 10.0.23.0/30 | 2001:db8:10:23::/64 |
| R3–R4 | 10.0.34.0/30 | 2001:db8:10:34::/64 |
| R1–R4 | 10.0.14.0/30 | 2001:db8:10:14::/64 |
| R4–R5 | 10.0.45.0/30 | 2001:db8:10:45::/64 |

---

## 🔒 Basic Security Implementation

Each router uses **local login authentication** with encrypted passwords to prevent unauthorized access.


### Applied on all routers:

enable
configure terminal
service password-encryption
enable secret cisco123
line console 0
password class123
login
line vty 0 4
password class123
login
transport input ssh telnet
exit
banner motd # UNAUTHORIZED ACCESS IS PROHIBITED #
end
write memory


---

## ⚙️ Features Configured

✅ VLAN configuration on all switches  
✅ Router-on-a-stick inter-VLAN routing  
✅ IPv4 DHCP and DHCPv6 for VLAN10 on each router  
✅ dynamic IPs for servers in VLAN20  
✅ OSPF and OSPFv3 routing across all routers  
✅ IPv6 addressing and unicast routing  
✅ DNS and HTTP on central server  
✅ Basic router security (console, VTY, enable secret)  
✅ DCE clock rate set on required serial links  

---

## 🧱 Configuration Steps Summary

### 1️⃣ Physical Cabling
Follow the cabling exactly as per the network plan:
R1 S0/0/0 ↔ R2 S0/0/0
R2 S0/0/1 ↔ R3 S0/0/0
R3 S0/0/1 ↔ R4 S0/0/0
R1 S0/0/1 ↔ R4 S0/0/1
R4 S0/1/0 ↔ R5 S0/0/0

LAN cabling connects router Gig0/0 interfaces to switches and PCs as per port mapping.

---

### 2️⃣ Router Configuration
- Set hostnames and disable DNS lookup
- Configure router-on-a-stick subinterfaces
- Configure IPv4 and IPv6 addressing
- Enable OSPF (IPv4) and OSPFv3 (IPv6)
- Create DHCPv4 and DHCPv6 pools for VLAN10
- Secure routers with passwords and encryption
- Save configuration with `write memory`

---

### 3️⃣ Switch Configuration
- Create VLAN 10 and VLAN 20
- Assign trunk to router link port
- Assign access ports to VLANs
- Enable spanning-tree portfast
- Set default gateway to the router’s VLAN20 IP

---

### 4️⃣ Server Configuration
**Server1 (S1 VLAN20)**  
- IP: `192.168.11.10` / Gateway: `192.168.11.1`
- DNS + HTTP enabled  
- Add DNS record: `www.example.com → 192.168.11.10`

**Server3 (S5 VLAN20)**  
- IP: `192.168.15.10` / Gateway: `192.168.15.1`

---

### 5️⃣ PC Configuration
- Set to **DHCP (IPv4)** and **Auto Config (IPv6)**
- Verify address acquisition:

  - Test connectivity:
ping 192.168.11.10
ping 192.168.15.10
ping 2001:db8:5::1


---

## 🧪 Verification Commands

Run these commands on routers to verify:
show ip interface brief
show ip route
show ip ospf neighbor
show ipv6 interface brief
show ipv6 route
show ipv6 ospf neighbor
show running-config
show ip dhcp binding


---

## 🧠 Learning Outcomes

By completing this project, you’ll learn to:
- Design and build a hybrid topology network.
- Configure inter-VLAN routing using subinterfaces.
- Implement dual-stack (IPv4/IPv6) connectivity.
- Deploy dynamic addressing via DHCP.
- Configure OSPF and OSPFv3 routing protocols.
- Apply essential router security configurations.
- Verify and troubleshoot connectivity using Cisco CLI.

---

## 🧾 Author
**Student:** Kebarileng Makgobe (Keba)  
**Course:** Bsc computer science with electronics  — *Networking Lab Project*  
**Institution:** North-West University  
**Tool Used:** Cisco Packet Tracer  

---

## 📦 How to Use
1. Open **Cisco Packet Tracer**.
2. Recreate the topology and apply the CLI configurations in order.
3. Start each device and verify connectivity.
4. Save your project as `Hybrid_Topology_Final.pkt`.
5. Upload your `.pkt` file and this `README.md` to your GitHub repository.

---

⭐ *This project demonstrates professional multi-protocol network configuration with VLANs, IPv4, IPv6, DHCP,DHCP6, OSPF, and security — ideal for academic and portfolio presentation.*



