## 📌 Project Overview

This project demonstrates the design and implementation of a small campus network using Cisco Packet Tracer.

The network is segmented into multiple VLANs to separate different user groups. Router-on-a-Stick (ROAS) is used to provide Inter-VLAN Routing between the VLANs.

This project was created to strengthen practical networking skills including VLAN configuration, trunking, IPv4 addressing, routing, DHCP, connectivity testing, and network troubleshooting.

---

## 🎯 Objectives

- Design a small campus network
- Segment users using VLANs
- Configure access ports
- Configure an 802.1Q trunk
- Configure a native VLAN
- Implement Router-on-a-Stick
- Enable Inter-VLAN Routing
- Configure IPv4 addressing and default gateways
- Configure DHCP
- Verify network connectivity
- Practice basic network troubleshooting

---

## 🖥️ Network Topology

The network consists of:

- 1 Cisco Router
- 1 Cisco Switch
- 1 Admin PC
- 1 Student PC
- 1 Guest PC

Topology:

                Router R1
                  G0/0
                    |
               802.1Q Trunk
                    |
                  G0/1
                Switch S1
             /       |       \
          F0/1     F0/2     F0/3
           |         |         |
        Admin PC  Student PC  Guest PC
        VLAN 10    VLAN 20    VLAN 30

---

## 🏷️ VLAN Design

| VLAN | Name | Purpose | Switch Port |
|------|------|---------|-------------|
| 10 | ADMIN | Administrative users | Fa0/1 |
| 20 | STUDENT | Student users | Fa0/2 |
| 30 | GUEST | Guest users | Fa0/3 |
| 99 | MANAGEMENT | Management / Native VLAN | Native VLAN |

Switch Gi0/1 is configured as an 802.1Q trunk carrying VLANs 10, 20, 30 and 99.

---

## 🌐 IP Addressing Plan

| VLAN | Network | Default Gateway |
|------|---------|-----------------|
| VLAN 10 | 192.168.10.0/24 | 192.168.10.1 |
| VLAN 20 | 192.168.20.0/24 | 192.168.20.1 |
| VLAN 30 | 192.168.30.0/24 | 192.168.30.1 |
| VLAN 99 | 192.168.99.0/24 | 192.168.99.1 |

Each VLAN uses a separate IPv4 subnet to maintain Layer 2 segmentation while allowing controlled Layer 3 communication through the router.

---

## ⚙️ Key Configuration

### VLAN Configuration

VLANs 10, 20, 30 and 99 were created on the switch.

Access ports were assigned according to their respective user groups.

### Trunk Configuration

The connection between the switch and router is configured as an 802.1Q trunk.

Allowed VLANs:

- VLAN 10
- VLAN 20
- VLAN 30
- VLAN 99

VLAN 99 is configured as the native VLAN.

### Router-on-a-Stick

Router subinterfaces are used to provide a Layer 3 gateway for each VLAN:

- G0/0.10 → VLAN 10
- G0/0.20 → VLAN 20
- G0/0.30 → VLAN 30
- G0/0.99 → VLAN 99

Each subinterface uses 802.1Q encapsulation and acts as the default gateway for its VLAN.

---

## 📡 DHCP

DHCP will be configured to automatically provide end devices with:

- IPv4 address
- Subnet mask
- Default gateway
- DNS server

> Status: In Progress

---

## ✅ Verification

The following commands are used to verify the network:

### Switch

    show vlan brief
    show interfaces trunk

### Router

    show ip interface brief
    show ip route

### End Devices

    ping <destination-IP>

Inter-VLAN connectivity between the Admin and Student VLANs has been successfully tested.

A first ping may occasionally time out while ARP resolves the destination MAC address. Subsequent successful replies confirm connectivity.

---

## 🔧 Troubleshooting Skills

This project also practices a structured troubleshooting process:

1. Check physical/interface status
2. Verify VLAN membership
3. Verify trunk configuration
4. Verify router subinterfaces and routing table
5. Verify end-device IP configuration
6. Test connectivity using ping

Common issues investigated include:

- Incorrect VLAN assignment
- VLAN missing from trunk allowed list
- Native VLAN mismatch
- Incorrect IP address
- Incorrect default gateway
- Router interface shutdown
- Incorrect 802.1Q encapsulation

---

## 📚 Skills Demonstrated

- Cisco Packet Tracer
- Cisco IOS
- VLAN Configuration
- Access Ports
- IEEE 802.1Q Trunking
- Native VLAN
- IPv4 Addressing
- Subnetting
- Router-on-a-Stick
- Inter-VLAN Routing
- DHCP
- Network Verification
- Network Troubleshooting

---

## 🚧 Project Status

**In Progress**

Completed:
- Network topology
- VLAN creation
- Access port configuration
- Trunk configuration
- Native VLAN configuration
- Router-on-a-Stick
- Inter-VLAN Routing
- Static IPv4 addressing
- Initial connectivity testing

Next:
- Complete DHCP configuration
- Verify DHCP addressing
- Complete connectivity testing between all VLANs
- Perform troubleshooting scenarios
- Capture verification screenshots
- Finalize project documentation

---

## 💡 Lessons Learned

Through this project, I learned how VLANs logically separate a switched network into different broadcast domains and how trunk links transport traffic from multiple VLANs using IEEE 802.1Q.

I also gained practical experience implementing Router-on-a-Stick, where multiple router subinterfaces provide Layer 3 gateways for different VLANs through a single physical router interface.

The project also reinforced the importance of systematic troubleshooting by verifying Layer 2 configuration, trunking, Layer 3 routing, IP addressing, and end-to-end connectivity.

---

## 👤 Author

BSc (Hons) Information Technology  
Computer Networking and Security  
Sunway University
