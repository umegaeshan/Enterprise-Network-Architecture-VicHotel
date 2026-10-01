# 🏨 Vic Modern Hotel - Enterprise Network Architecture

![Network Topology](Screenshot_2026-10-02_000829.png)

## 📌 Project Overview
This project is a comprehensive, three-floor enterprise network architecture designed for the **Vic Modern Hotel**. It was implemented using **Cisco Packet Tracer** as a hands-on project to demonstrate advanced networking concepts. The architecture ensures high availability, security, and scalable communication across various hotel departments.

This project was completed as part of the **Information and Communication Technology (ICT)** degree program at the **University of Colombo, Faculty of Technology**.

## 🚀 Key Technologies & Features Implemented
* **Dynamic Routing (OSPF):** Configured Single-Area OSPF (Area 0) for dynamic route discovery across three routers using `/30` WAN subnets.
* **VLAN Segmentation:** Designed 8 logical networks (VLANs 10-80) to isolate departmental traffic and improve network efficiency.
* **Inter-VLAN Routing:** Implemented *Router-on-a-Stick (ROAS)* using sub-interfaces with 802.1Q encapsulation.
* **DHCP Services:** Configured centralized DHCP pools on routers to dynamically allocate IP addresses to End Devices.
* **Network Security:** 
  * Implemented **Port Security (Sticky MAC)** with shutdown violation modes to prevent unauthorized access.
  * Configured **SSH** for secure remote administration of network devices.
* **Wireless Networking:** Integrated Access Points (APs) with isolated SSIDs for laptops and smart devices.

---

## 📊 IP Addressing & VLAN Scheme

### 🏢 Floor 3 (Router: FR3)
| Department | VLAN ID | Network Address | Subnet Mask | Default Gateway |
| :--- | :---: | :--- | :--- | :--- |
| **IT** | 10 | 192.168.1.0 | 255.255.255.0 | 192.168.1.1 |
| **Admin** | 20 | 192.168.2.0 | 255.255.255.0 | 192.168.2.1 |

### 🏢 Floor 2 (Router: FR2)
| Department | VLAN ID | Network Address | Subnet Mask | Default Gateway |
| :--- | :---: | :--- | :--- | :--- |
| **Finance** | 30 | 192.168.3.0 | 255.255.255.0 | 192.168.3.1 |
| **HR** | 40 | 192.168.4.0 | 255.255.255.0 | 192.168.4.1 |
| **Sales** | 50 | 192.168.5.0 | 255.255.255.0 | 192.168.5.1 |

### 🏢 Floor 1 (Router: FR1)
| Department | VLAN ID | Network Address | Subnet Mask | Default Gateway |
| :--- | :---: | :--- | :--- | :--- |
| **Reception**| 60 | 192.168.6.0 | 255.255.255.0 | 192.168.6.1 |
| **Store** | 70 | 192.168.7.0 | 255.255.255.0 | 192.168.7.1 |
| **Logistics**| 80 | 192.168.8.0 | 255.255.255.0 | 192.168.8.1 |

### 🌐 WAN Links (Point-to-Point /30)
| Link | Network Address | Subnet Mask | FR1 IP | FR2 IP | FR3 IP |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **FR3 to FR2** | 10.10.10.0 | 255.255.255.252 | - | 10.10.10.2 | 10.10.10.1 |
| **FR3 to FR1** | 10.10.10.4 | 255.255.255.252 | 10.10.10.6 | - | 10.10.10.5 |
| **FR2 to FR1** | 10.10.10.8 | 255.255.255.252 | 10.10.10.10| 10.10.10.9 | - |

---

## 🛠️ Testing & Verification
The network was heavily tested to ensure full connectivity and security compliance.

* **OSPF Routing Table:**
  Successful establishment of OSPF neighbor adjacencies, dynamically learning routes across all subnets (`show ip route`).
  *(See Screenshot_2026-10-02_001828.png)*

* **End-to-End Connectivity:**
  Successful ICMP ping requests passing across multiple floors/VLANs (e.g., Ping to `192.168.6.2`).
  *(See Screenshot_2026-10-02_001702.png)*

## 💻 How to Run This Project
1. Clone this repository or download the ZIP file.
2. Ensure you have **Cisco Packet Tracer** installed (Version 8.0 or higher recommended).
3. Open the `Vic Modern Hotel.pkt` file.
4. Interact with the PCs, view the router routing tables (`show ip route`), and test connectivity using the command prompt.

---
*Created by an ICT Undergraduate at the University of Colombo.* 🎓