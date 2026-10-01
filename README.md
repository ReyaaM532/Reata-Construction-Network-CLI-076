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


  

| VLAN | Network Address  | Subnet Mask       | Broadcast Address | Default Gateway  | Assignable Host Range             |
| ---: | ---------------- | ----------------- | ----------------- | ---------------- | --------------------------------- |
|   10 | `192.168.38.0`   | `255.255.255.224` | `192.168.38.31`   | `192.168.38.1`   | `192.168.38.2 – 192.168.38.30`    |
|   20 | `192.168.38.32`  | `255.255.255.224` | `192.168.38.63`   | `192.168.38.33`  | `192.168.38.34 – 192.168.38.62`   |
|   30 | `192.168.38.64`  | `255.255.255.224` | `192.168.38.95`   | `192.168.38.65`  | `192.168.38.66 – 192.168.38.94`   |
|   40 | `192.168.38.96`  | `255.255.255.224` | `192.168.38.127`  | `192.168.38.97`  | `192.168.38.98 – 192.168.38.126`  |
|   50 | `192.168.38.128` | `255.255.255.224` | `192.168.38.159`  | `192.168.38.129` | `192.168.38.130 – 192.168.38.158` |
|   60 | `192.168.38.160` | `255.255.255.224` | `192.168.38.191`  | `192.168.38.161` | `192.168.38.162 – 192.168.38.190` |


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
 
