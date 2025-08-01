# LAN Scenario 03 – Static Routing Between Two Networks

## 🎯 Objective
This lab demonstrates how to connect two separate LANs using two routers and static routing, allowing end devices to communicate across networks.

## 🧱 Devices Used
- 2× Cisco Routers (e.g. 2911)
- 2× Switches
- 4× PCs (2 per LAN)
- Copper Straight-through cables (for PC ↔ Switch and Switch ↔ Router)
- Crossover cable (for Router ↔ Router)

## 🧠 Network Topology

 Segment          Network         Subnet Mask      Devices         
--------------------------------------------------------------------
 LAN 1 (Left)     10.0.1.024      255.255.255.0     PC0, PC1        
 LAN 2 (Right)    10.0.2.024      255.255.255.0     PC2, PC3        
 Inter-Router     192.168.1.030   255.255.255.252   Router0↔Router1 

## 📐 Topology

![Topology Screenshot](.topology.PNG)

## 🌐 IP Address Configuration

 Device      Interface        IP Address       Subnet           
------------------------------------------------------------------
 PC0         —                10.0.1.10        255.255.255.0    
 PC1         —                10.0.1.11        255.255.255.0    
 PC2         —                10.0.2.10        255.255.255.0    
 PC3         —                10.0.2.11        255.255.255.0    
 Router0     Gig01           10.0.1.1         255.255.255.0    
 Router0     Gig00           192.168.1.1      255.255.255.252  
 Router1     Gig01           10.0.2.1         255.255.255.0    
 Router1     Gig00           192.168.1.2      255.255.255.252  

## 🔧 Static Routing Configuration

### Router0
```bash
interface gig01
 ip address 10.0.1.1 255.255.255.0
 no shutdown
!
interface gig00
 ip address 192.168.1.1 255.255.255.252
 no shutdown
!
ip route 10.0.2.0 255.255.255.0 192.168.1.2
