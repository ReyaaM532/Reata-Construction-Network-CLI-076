\# Network Topology



\## Network Structure



The network consists of the following main components:



\- Cloud PT representing the external Internet network

\- Cisco 2911 Router providing external network connectivity

\- Cisco 3560 Multilayer Switch providing Layer 3 switching, inter-VLAN routing, DHCP services, and ACL implementation

\- Cisco 2960 Access Switch providing Layer 2 connectivity to end devices

\- Wireless Access Point providing Guest Wi-Fi connectivity

\- End devices including departmental PCs, printers and guest wireless clients



\## VLAN Structure



| VLAN | Department | Subnet |

|---|---|---|

| 10 | Management | 192.168.38.0/27 |

| 20 | HR | 192.168.38.32/27 |

| 30 | Finance | 192.168.38.64/27 |

| 40 | Procurement | 192.168.38.96/27 |

| 50 | Engineering | 192.168.38.128/27 |

| 60 | Health \& Safety | 192.168.38.160/27 |

| 70 | Guest Wi-Fi | 192.168.38.192/27 |



\## Topology Design



The multilayer switch acts as the central network device and provides the default gateways for the VLANs. Departmental devices are connected through access ports assigned to their respective VLANs.



The connection between the multilayer switch and the access switch carries the required VLAN traffic. Guest Wi-Fi traffic is assigned to VLAN 70 and is controlled using an ACL that prevents access to internal departmental networks.



\## Security



The network uses VLAN segmentation and access control to separate departmental traffic. The Guest VLAN is restricted from accessing internal departmental VLANs, while SSH is enabled on the multilayer switch for secure remote management.



\## Evidence



Network topology screenshots are stored in this folder and provide visual evidence of the implemented Cisco Packet Tracer network design.

