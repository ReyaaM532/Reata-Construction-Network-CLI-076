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

  The network components are:

  - **Cloud PT**
  - **Cisco 3560 Multilayer 3 Switch** 
  - **Cisco 2960 Access Switch**
  - **Router 2911**
  - **Guest Wireless Access Point**
  - **End Devices**


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

The address range `192.168.38.224/27` (`192.168.38.224 – 192.168.38.255`) is reserved for future expansion.

This reserved address space supports the client requirement that a branch office may be opened within 18 months.

 
## VLAN Configuration

VLANs were implemented to logically separate the departments and Guest Wi-Fi network. Each VLAN is associated with a dedicated `/27` subnet from the assigned `192.168.38.0/24` addressing block.

| VLAN | Name | Purpose |
|------|------|---------|
| 10 | Management | Management department |
| 20 | HR | Human Resources |
| 30 | Finance | Finance department |
| 40 | Procurement | Procurement department |
| 50 | Engineering | Engineering department |
| 60 | Health & Safety | Health and Safety department |
| 70 | Guest Wi-Fi | Guest and visitor wireless access |

### VLAN Gateway Configuration

The default gateway for each VLAN is configured on the Layer 3.

| VLAN | Default Gateway |
|------|-----------------|
| 10 | `192.168.38.1` |
| 20 | `192.168.38.33` |
| 30 | `192.168.38.65` |
| 40 | `192.168.38.97` |
| 50 | `192.168.38.129` |
| 60 | `192.168.38.161` |
| 70 | `192.168.38.193` |

### Access Port Allocation

The departmental access ports were configured according to the VLAN requirements:

| Switch Port | VLAN | Network |
|-------------|------|---------|
| Fa0/1 | 70 | Guest Wi-Fi |
| Fa0/2 | 10 | Management |
| Fa0/3 | 20 | HR |
| Fa0/4 | 30 | Finance |
| Fa0/5 | 40 | Procurement |
| Fa0/6 | 50 | Engineering |
| Fa0/7 | 60 | Health & Safety |

The link between the multilayer switch and the router is configured as a **802.1Q trunk**.


## Access Control List (ACL) Configuration

An Extended Access Control List (ACL) was implemented to restrict Guest Wi-Fi users from accessing Sensitive departments.

The Guest Wi-Fi network uses **VLAN 70** with the subnet `192.168.38.192/27`. The ACL is applied inbound on the VLAN 70 interface of the multilayer switch.

The ACL denies traffic from the Guest Wi-Fi network to the following internal departmental VLANs:

- Management – `192.168.38.0/27`
- HR – `192.168.38.32/27`
- Finance – `192.168.38.64/27`
- Procurement – `192.168.38.96/27`
- Engineering – `192.168.38.128/27`
- Health & Safety – `192.168.38.160/27`

Traffic from the Guest Wi-Fi network to other destinations is permitted.

This ACL(which is a technical challenge) configuration provides network segmentation and prevents guest users from accessing internal departmental resources while still allowing Guest Wi-Fi connectivity to external networks.


## DHCP Configuration

DHCP was configured on the 3560 multilayer switch to assign IP addresses to devices connected to the Guest Wi-Fi network.

The Guest Wi-Fi network uses **VLAN 70** and the `192.168.38.192/27` subnet.

### Guest DHCP Configuration

| Parameter | Configuration |
|-----------|---------------|
| DHCP Pool | `GUEST` |
| Network | `192.168.38.192/27` |
| Default Gateway | `192.168.38.193` |
| DNS Server | `8.8.8.8` |
| Excluded Address | `192.168.38.193` |

DHCP allows Guest Wi-Fi devices to obtain the required IP configuration without manual addressing.


## Secure Remote Management – SSH

Secure remote management was implemented using **SSH (Secure Shell)** on the Cisco 3560 multilayer switch.

SSH provides an encrypted method for remotely managing network devices and is more secure than Telnet.

### SSH Configuration

The multilayer switch was configured with:

- A hostname for the network device
- A domain name
- A local administrator account
- RSA cryptographic keys
- SSH version 2
- Local authentication on the VTY lines
- SSH as the only permitted remote access protocol


## Testing and Evidence

Network testing was conducted in Cisco Packet Tracer to verify connectivity, VLAN segmentation, DHCP, ACL restrictions, and secure remote management.

Detailed testing results and supporting screenshots.


## Troubleshooting

Configuration and connectivity issues encountered during implementation were investigated and resolved. Detailed troubleshooting steps and supporting evidence are provided in the `Troubleshooting/` folder.

 ## Default Test Credentials

To test safe SSH remote management, the administrator account listed below was utilized.

| Credential | Value |
|------------|-------|
| Username | `admin` |
| Privilege Level | 15 |
| Access Method | SSH |


 
