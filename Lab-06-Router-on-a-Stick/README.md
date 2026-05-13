# Lab 06 — Router-on-a-Stick Inter-VLAN Routing

## Objective
Configure inter-VLAN routing using Router-on-a-Stick with 802.1Q trunking and router subinterfaces.

---

## Technologies Used
- Cisco Packet Tracer
- VLANs
- 802.1Q Trunking
- Router Subinterfaces
- Inter-VLAN Routing
- IPv4 Addressing

---

## Network Overview
- VLAN 10 — SALES
- VLAN 20 — IT
- Router-on-a-Stick topology
- Trunk link between switch and router

---

## Tasks Completed
- Created VLAN 10 and VLAN 20
- Assigned switch access ports to VLANs
- Configured trunk port
- Configured router subinterfaces
- Assigned IP addresses
- Configured PC default gateways
- Tested inter-VLAN communication
- Verified routing and trunking

---

## Configuration Steps

### Step 1 — Configure VLANs on Switch

```bash
enable
conf t

vlan 10
name SALES
exit

vlan 20
name IT
exit
```

---

### Step 2 — Configure Access Ports

```bash
interface range fa0/1 - 2
switchport mode access
switchport access vlan 10
exit

interface range fa0/3 - 4
switchport mode access
switchport access vlan 20
exit
```

---

### Step 3 — Configure Trunk Port

```bash
interface g0/1
switchport mode trunk
exit
```

---

### Step 4 — Configure Router Physical Interface

```bash
enable
conf t

interface g0/0
no shutdown
exit
```

---

### Step 5 — Configure VLAN 10 Subinterface

```bash
interface g0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit
```

---

### Step 6 — Configure VLAN 20 Subinterface

```bash
interface g0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
exit
```

---

### Step 7 — Configure PCs

| Device | IP Address | Default Gateway |
|---|---|---|
| PC1 | 192.168.10.10 | 192.168.10.1 |
| PC2 | 192.168.10.11 | 192.168.10.1 |
| PC3 | 192.168.20.10 | 192.168.20.1 |
| PC4 | 192.168.20.11 | 192.168.20.1 |

---

### Step 8 — Connectivity Testing

From PC1:

```bash
ping 192.168.20.10
```

Expected Result:
- Successful inter-VLAN communication

---

## Verification Commands

### Switch

```bash
show vlan brief
show interfaces trunk
```

### Router

```bash
show ip interface brief
```

---

## Result
Successful communication between VLAN 10 and VLAN 20 using Router-on-a-Stick inter-VLAN routing.

---

## Skills Demonstrated
- VLAN configuration
- Trunking
- Router subinterfaces
- Inter-VLAN routing
- Cisco CLI
- Network troubleshooting
- Layer 2 and Layer 3 networking

---

## Lab Summary
- Configured VLAN 10 and VLAN 20 on the switch
- Assigned access ports to VLANs
- Configured an 802.1Q trunk between the switch and router
- Enabled the router physical interface
- Configured router subinterfaces for inter-VLAN routing
- Assigned IP addresses to router subinterfaces
- Configured default gateways on PCs
- Enabled communication between VLANs using Router-on-a-Stick
- Verified trunking and routing functionality
- Tested successful inter-VLAN connectivity using ping
- Learned Layer 3 routing between VLANs
- Saved switch and router configurations
