# Reata Construction Group Network - CLI-076

## Project Overview

This computer network is designed for **Reata Construction Group**, with a focus on network segmentation, access control, and secure remote management.

The network implements **Access Control Lists (ACLs)** as the technical challenge and also addresses the client's change request requiring **one off-site administrator to have secure remote management access to network devices**.

The IP addressing plan also reserves address space to support the constraint that a **branch office may be opened within 18 months**, allowing the network to accommodate future expansion.

The network is designed, configured, and tested using **Cisco Packet Tracer**, with supporting evidence covering the client requirements, network design, IP addressing, topology, configuration, testing, troubleshooting, and project reflection.

# Client Background and Requirements

- **Client ID:** CLI-076
- **Organisation:** Reata Construction Group (Potchefstroom)
- **Industry:** Construction
- **Assigned Addressing Block:** `192.168.38.0/24`
- **Technical Challenge:** ACLs (traffic filtering policy)
- **Constraint:** A branch office may be opened within 18 months.
- **Change Request – CR9:** One off-site administrator requires secure remote management access to network devices.



## Network Design

  VLANS separate the different organisation departments and the Guest network.

  The network components are:

  - **Cisco 3560 Multilayer 3 Switch:** Provides inter-VLAN routing, VLAN gateways, ACL implementation, and network management.
  - **Cisco 2960 Access Switch:** Provides layer 2 connectivity for end devices.
  - **Router 2911:** Provides connectivity between the internal network and the external network.
  - **Guest Wireless Access Point:** Provides wireless connectivity for visitors through Guest VLAN.
  - **End Devices:** PCs, printers, and email server are connected to appropriate vlans.


## IP Addressing Plan

The assigned addressing block for the project is `192.168.38.0/24`. The network is divided into `/27` subnets to provide separate address ranges for each VLAN while allowing for future expansion.

Each `/27` subnet provides **32 total addresses**, including **30 usable host addresses**.

| VLAN | Department | Network Address | Default Gateway | Usable Host Range | Broadcast |
|------|------------|-----------------|-----------------|-------------------|-----------|
| 10 | Management | `192.168.38.0/27` | `192.168.38.1` | `192.168.38.2 – 192.168.38.30` | `192.168.38.31` |
| 20 | HR | `192.168.38.32/27` | `192.168.38.33` | `192.168.38.34 – 192.168.38.62` | `192.168.38.63` |
| 30 | Finance | `192.168.38.64/27` | `192.168.38.65` | `192.168.38.66 – 192.168.38.94` | `192.168.38.95` |
| 40 | Procurement | `192.168.38.96/27` | `192.168.38.97` | `192.168.38.98 – 192.168.38.126` | `192.168.38.127` |
| 50 | Engineering | `192.168.38.128/27` | `192.168.38.129` | `192.168.38.130 – 192.168.38.158` | `192.168.38.159` |
| 60 | Health & Safety | `192.168.38.160/27` | `192.168.38.161` | `192.168.38.162 – 192.168.38.190` | `192.168.38.191` |
| 70 | Guest Wi-Fi | `192.168.38.192/27` | `192.168.38.193` | `192.168.38.194 – 192.168.38.222` | `192.168.38.223` |



## Reserved Address Space

The remaining address space from:

192.168.38.192 – 192.168.38.255

is reserved for future expansion

 

## Connectivity Testing
 The network is tested in Cisco Packet Tracer to verify that the design meets the client's requirements.

Ping tests are performed between devices in the same VLAN.

show vlan brief

show ip interface brief


## Security 



Security Measures includes:

VLAN segmentation

Password protection

Encrypted passwords

SSH-based remote management

Access Control Lists


 ## Project Structure

 -Ip-addressing 

 -Configurations

 -Diagrams

 -Packet Tracer

 -Screenshots

 -Documentation
 
