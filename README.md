# hybrid-topology
Hybrid Topology Project with VLANs, IPv4, IPv6, DHCP, OSPF, and basic router security.

# 🌐 Hybrid Topology Network Configuration (IPv4 + IPv6 + VLANs + Security)

## 📁 Repository Structure
CMPG325-Hybrid-Topology/
│
├── 📄 README.md # Project Documentation
├── 🗂️ Topologies/ # Individual Topology Designs
│ ├── Bus/
│ ├── Mesh/
│ ├── Star/
│ ├── Ring/
│ ├── Extended-Star/
│ └── Hybrid/
│
├── ⚙️ Configurations/ # Device Configuration Files
│ ├── Router-configs/
│ ├── Switch-configs/
│ └── Server-configs/
│
├── 🖼️ Screenshots/ # Evidence & Testing
│ ├── Topology-views/
│ ├── Ping-tests/
│ ├── DHCPv6-working/
│ └── OSPF-neighbors/
│
└── 🔧 Hybrid_Topology_Final.pkt # Cisco Packet Tracer File

---

## 👤 Student Information
| **Field** | **Details** |
|------------|-------------|
| **Name** | Kebarileng Makgobe (Keba) |
| **Course** | BSc Computer Science with Electronics |
| **Institution** | North-West University |
| **Course Code** | CMPG 325 - Computer Networks |
| **Academic Year** | 2025 |

---

## 🎯 Project Overview
This project implements a **hybrid network topology** that integrates multiple architecture types. It demonstrates advanced network engineering principles through **dual-stack IPv4/IPv6 deployment**, **VLAN segmentation**, **OSPF routing**, **DHCPv6 dynamic addressing**, and **enterprise-grade security hardening**.

---

## 📊 Network Architecture

### 🔷 Topology Design
- **Type:** Hybrid (Star + Mesh + Bus elements)  
- **Scale:** 5 Routers, 5 Switches, 12 End Devices  
- **Protocols:** OSPFv2, OSPFv3, DHCP, DHCPv6

### 🏗️ Physical Layout
                          ┌──────────┐
                          │   R2     │
                          └───┬───┬───┘
                              │   │
                 ┌────────────┘   └────────────┐
                 │                             │
             ┌───┴───┐                     ┌───┴───┐
             │   R1   │                     │   R3   │
             └───┬───┘                     └───┬───┘
                 │                               │
         ┌───────┘                               │
         │                                       │
     ┌───┴───┐                              ┌────┴────┐
     │   S1   │                              │   S3    │
     └───┬────┘                              └────┬────┘
   ┌─────┴──────┐                           ┌─────┴──────┐
   │             │                           │            │
┌──────┐    ┌──────┐                    ┌──────┐     ┌──────┐
│ PC1  │    │Server│                    │ PC3  │     │Server│
│ VLAN10│   │ VLAN20│                    │VLAN10│    │VLAN20│
└──────┘    └──────┘                    └──────┘     └──────┘


                              ┌──────────┐
                              │   R4     │
                              └───┬───┬───┘
                                  │   │
                                  │   └────────────┐
                                  │                │
                             ┌────┴────┐       ┌───┴───┐
                             │   S4    │       │   R5   │
                             └────┬────┘       └───┬───┘
                                  │                │
                            ┌─────┴──────┐     ┌───┴────┐
                            │    PC4     │     │ Switch5 │
                            │  VLAN10    │     └────┬────┘
                                                 │
                 ┌──────────────┬──────────────┬──┴──┬────────────┐
                 │              │              │     │            │
              ┌──────┐      ┌──────┐      ┌──────┐  ┌──────┐  ┌──────┐
              │ PC5  │      │ PC6  │      │ PC7  │  │ PC8  │  │ PC9  │
              │VLAN10│      │VLAN10│      │VLAN10│  │VLAN10│  │VLAN10│
              └──────┘      └──────┘      └──────┘  └──────┘  └──────┘
                                                     │
                                                 ┌──────┐
                                                 │Server│
                                                 │VLAN20│
                                                 └──────┘


### 🔌 Device Inventory
| **Device Type** | **Quantity** | **Role** |
|-----------------|--------------|----------|
| Routers | 5 | Core Routing & Inter-VLAN |
| Switches | 5 | VLAN Segmentation |
| PCs | 9 | End User Workstations |
| Servers | 3 | DNS, HTTP, DHCP Services |

---

## 🌐 IP Addressing Scheme

### 📋 IPv4 Addressing Table
| Device | Interface | IP Address | Subnet Mask | Gateway | VLAN |
|--------|-----------|------------|-------------|---------|------|
| R1 | G0/0.10 | 192.168.1.1 | 255.255.255.0 | N/A | 10 |
| R1 | G0/0.20 | 192.168.11.1 | 255.255.255.0 | N/A | 20 |
| R2 | G0/0.10 | 192.168.2.1 | 255.255.255.0 | N/A | 10 |
| R2 | G0/0.20 | 192.168.12.1 | 255.255.255.0 | N/A | 20 |
| R3 | G0/0.10 | 192.168.3.1 | 255.255.255.0 | N/A | 10 |
| R3 | G0/0.20 | 192.168.13.1 | 255.255.255.0 | N/A | 20 |
| R4 | G0/0.10 | 192.168.4.1 | 255.255.255.0 | N/A | 10 |
| R4 | G0/0.20 | 192.168.14.1 | 255.255.255.0 | N/A | 20 |
| R5 | G0/0.10 | 192.168.5.1 | 255.255.255.0 | N/A | 10 |
| R5 | G0/0.20 | 192.168.15.1 | 255.255.255.0 | N/A | 20 |

### 🔷 IPv6 Addressing Table
| Device | Interface | IPv6 Address | Prefix | Gateway | VLAN |
|--------|-----------|--------------|--------|---------|------|
| R1 | G0/0.10 | 2001:db8:1::1 | /64 | N/A | 10 |
| R1 | G0/0.20 | 2001:db8:1:10::1 | /64 | N/A | 20 |
| R2 | G0/0.10 | 2001:db8:2::1 | /64 | N/A | 10 |
| R2 | G0/0.20 | 2001:db8:2:10::1 | /64 | N/A | 20 |
| R3 | G0/0.10 | 2001:db8:3::1 | /64 | N/A | 10 |
| R3 | G0/0.20 | 2001:db8:3:10::1 | /64 | N/A | 20 |
| R4 | G0/0.10 | 2001:db8:4::1 | /64 | N/A | 10 |
| R4 | G0/0.20 | 2001:db8:4:10::1 | /64 | N/A | 20 |
| R5 | G0/0.10 | 2001:db8:5::1 | /64 | N/A | 10 |
| R5 | G0/0.20 | 2001:db8:5:10::1 | /64 | N/A | 20 |

### 🏷️ VLAN Configuration
| VLAN ID | Name | IPv4 Subnet | IPv6 Subnet | Purpose |
|----------|------|-------------|-------------|----------|
| 10 | Workstations | 192.168.x.0/24 | 2001:db8:x::/64 | User PCs |
| 20 | Servers | 192.168.1x.0/24 | 2001:db8:x:10::/64 | Network Services |

### 🔗 Serial Link Addressing
| Connection | IPv4 Subnet | IPv6 Subnet |
|-------------|-------------|-------------|
| R1 ↔ R2 | 10.0.12.0/30 | 2001:db8:10:12::/64 |
| R2 ↔ R3 | 10.0.23.0/30 | 2001:db8:10:23::/64 |
| R3 ↔ R4 | 10.0.34.0/30 | 2001:db8:10:34::/64 |
| R1 ↔ R4 | 10.0.14.0/30 | 2001:db8:10:14::/64 |
| R4 ↔ R5 | 10.0.45.0/30 | 2001:db8:10:45::/64 |

---

## ⚙️ Configuration Implementation

### 🔒 Router Security Configuration
```bash
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
banner motd # UNAUTHORIZED ACCESS IS PROHIBITED #
end
write memory

🌐 DHCPv6 Server Setup
configure terminal
ipv6 unicast-routing
ipv6 dhcp pool VLAN10_POOL
 address prefix 2001:DB8:1::/64
 dns-server 2001:DB8::1
exit
ipv6 dhcp pool VLAN20_POOL
 address prefix 2001:DB8:1:10::/64
 dns-server 2001:DB8::1
exit
interface GigabitEthernet0/0.10
 ipv6 dhcp server VLAN10_POOL
exit
interface GigabitEthernet0/0.20
 ipv6 dhcp server VLAN20_POOL
exit
end
write memory

✅ Testing & Verification
🧪 Connectivity Tests
| Test         | Source        | Destination                               | Result |
| ------------ | ------------- | ----------------------------------------- | ------ |
| Inter-VLAN   | PC1 (VLAN 10) | Server1 (VLAN 20)                         | ✅ PASS |
| Gateway      | PC1           | R1 G0/0.10                                | ✅ PASS |
| Cross-Router | R1            | R5                                        | ✅ PASS |
| IPv6         | PC1           | Server1 IPv6                              | ✅ PASS |
| DNS          | nslookup      | [www.example.com](http://www.example.com) | ✅ PASS |

🔍 Verification Commands
# Routing Verification
show ip route
show ipv6 route
# Protocol Status
show ip ospf neighbor
show ipv6 ospf neighbor
# Addressing & DHCP
show ip interface brief
show ipv6 interface brief
show ip dhcp binding
show ipv6 dhcp binding
# Configuration
show running-config

🚧 Challenges & Solutions

Challenge	Solution	Outcome

Challenge	Solution	Outcome
DHCPv6 address assignment failures Enabled ipv6 unicast-routing and verified pool assignments	✅ All PCs receive IPv6 addresses
OSPFv3 neighbor adjacencies not forming	Corrected interface assignments and area configurations	✅ Full OSPFv3 convergence
Inter-VLAN routing issues	Implemented router-on-a-stick with proper 802.1Q encapsulation	✅ Seamless cross-VLAN communication

📈 Feature Implementation Status
| Feature              | Status     | Verification             |
| -------------------- | ---------- | ------------------------ |
| VLAN Segmentation    | ✅ Complete | `show vlan brief`        |
| Inter-VLAN Routing   | ✅ Complete | Ping between VLANs       |
| Dual-Stack IPv4/IPv6 | ✅ Complete | Addressing confirmed     |
| DHCPv6 Services      | ✅ Complete | `show ipv6 dhcp binding` |
| OSPF/OSPFv3 Routing  | ✅ Complete | `show ip ospf neighbor`  |
| Router Security      | ✅ Complete | `show running-config`    |
| DNS & HTTP Services  | ✅ Complete | `nslookup` & web test    |

🧱 Configuration Steps Summary
1️⃣ Physical Cabling
R1 S0/0/0 ↔ R2 S0/0/0
R2 S0/0/1 ↔ R3 S0/0/0
R3 S0/0/1 ↔ R4 S0/0/0
R1 S0/0/1 ↔ R4 S0/0/1
R4 S0/1/0 ↔ R5 S0/0/0
Routers connect via serial links.
Each router connects to one switch via GigabitEthernet0/0.
VLANs connect end devices and servers.

2️⃣ Router Configuration Summary
Assign hostnames and disable DNS lookup
Configure subinterfaces for VLANs
Assign IPv4/IPv6 addresses
Enable OSPFv2 (IPv4) and OSPFv3 (IPv6)
Configure DHCPv4 & DHCPv6 pools for VLAN 10
Apply security (console, vty, enable secret)
Save configuration

3️⃣ Switch Configuration Summary
Create VLAN 10 and VLAN 20
Assign trunk to router interface
Assign access ports to VLANs
Enable spanning-tree portfast
Set default gateway (router’s VLAN20 IP)

4️⃣ Server Configuration
Server1 (S1 VLAN20)
IP: 192.168.11.10
Gateway: 192.168.11.1
DNS + HTTP enabled
DNS Record: www.example.com → 192.168.11.10

Server3 (S5 VLAN20)
IP: 192.168.15.10
Gateway: 192.168.15.1
DNS + HTTP enabled
DNS Record: www.myhrid.com → 192.168.15.10

5️⃣ PC Configuration
IPv4: DHCP
IPv6: Auto-config
Verify connectivity:
ping 192.168.11.10
ping 192.168.15.10
ping 2001:db8:5::1

🧠 Learning Outcomes

By completing this project, you will:
🧩 Design and build a hybrid network topology
🔗 Configure inter-VLAN routing
🌐 Implement dual-stack IPv4/IPv6 connectivity
📡 Deploy dynamic addressing (DHCP/DHCPv6)
🔁 Configure OSPF and OSPFv3
🔒 Apply essential router security
🧭 Verify and troubleshoot network connectivity

📦 How to Use
Open Cisco Packet Tracer.
Recreate or open the provided topology file.
Apply the CLI configurations as documented.
Verify connectivity and routing tables.
Save as Hybrid_Topology_Final.pkt.
Upload .pkt and README.md to your GitHub repository.

⭐ This project demonstrates professional, multi-protocol network configuration — featuring VLANs, IPv4, IPv6, DHCP/DHCPv6, OSPF, and router security — ideal for academic assessment and portfolio presentation.

