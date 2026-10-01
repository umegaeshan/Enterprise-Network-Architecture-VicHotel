# Enterprise Network Architecture - Vic Modern Hotel

![Network Topology](Screenshot_2026-10-02_000829.png)

## Overview
This repository contains a comprehensive 3-floor enterprise network architecture designed and implemented using Cisco Packet Tracer. The project simulates a real-world corporate hotel environment, integrating routing, switching, wireless connectivity, and network security. 

This project was developed as a practical implementation for the Information and Communication Technology degree program at the University of Colombo Faculty of Technology.

## Key Technologies & Protocols
*   **Dynamic Routing:** OSPF (Open Shortest Path First) configured across all routers using `/30` WAN links.
*   **VLAN Segmentation:** 8 isolated Virtual LANs deployed across three floors for departmental traffic separation.
*   **Inter-VLAN Routing:** Router-on-a-Stick configuration utilizing sub-interfaces and 802.1Q encapsulation.
*   **DHCP Services:** Routers configured as DHCP servers for automated IP address allocation across all VLANs.
*   **Network Security:** 
    *   Port Security implemented with Sticky MAC addresses and violation shutdown modes (tested via `Test-PC`).
    *   SSH configured on all routers for secure remote administration.
*   **Wireless Networking:** Access Points configured with floor-specific SSIDs to isolate mobile and laptop traffic.

## IP Addressing & VLAN Scheme

### Local Area Networks (LAN - /24)
| Floor | Department | VLAN ID | Network Address | Default Gateway |
| :--- | :--- | :--- | :--- | :--- |
| **3rd Floor** | IT | VLAN 10 | 192.168.1.0/24 | 192.168.1.1 |
| | Admin | VLAN 20 | 192.168.2.0/24 | 192.168.2.1 |
| **2nd Floor** | Finance | VLAN 30 | 192.168.3.0/24 | 192.168.3.1 |
| | HR | VLAN 40 | 192.168.4.0/24 | 192.168.4.1 |
| | Sales | VLAN 50 | 192.168.5.0/24 | 192.168.5.1 |
| **1st Floor** | Reception | VLAN 60 | 192.168.6.0/24 | 192.168.6.1 |
| | Store | VLAN 70 | 192.168.7.0/24 | 192.168.7.1 |
| | Logistics | VLAN 80 | 192.168.8.0/24 | 192.168.8.1 |

### Wide Area Networks (WAN - /30)
| Connection | Network Address | IP Configuration |
| :--- | :--- | :--- |
| 3rd Floor ⟷ 2nd Floor | 10.10.10.0/30 | Router 3: 10.10.10.1 <br> Router 2: 10.10.10.2 |
| 3rd Floor ⟷ 1st Floor | 10.10.10.4/30 | Router 3: 10.10.10.5 <br> Router 1: 10.10.10.6 |
| 2nd Floor ⟷ 1st Floor | 10.10.10.8/30 | Router 2: 10.10.10.9 <br> Router 1: 10.10.10.10 |

## How to Test the Project
1.  Download the `.pkt` file and open it in Cisco Packet Tracer (v8.0 or higher).
2.  **Verify Routing:** Access any router CLI and run `show ip route` to view OSPF learned routes (`O`).
3.  **Verify Security:** Attempt to connect a different device to the IT Switch `fa0/1` port to trigger the port security shutdown.
4.  **Verify SSH:** Open `Test-PC` (3rd Floor), open Command Prompt, and run `ssh -l admin 192.168.1.1` to access the router remotely.
5.  **Verify Connectivity:** Ping any PC from one floor to a completely different department on another floor.

## Author
**Umega Eshan**
