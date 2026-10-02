\# IP Addressing Plan



\## Network Address Block



The network uses the private IPv4 address block:



`192.168.38.0/24`



The `/24` network is divided into `/27` subnets. Each `/27` subnet provides 32 addresses, including 30 usable host addresses.



\## VLAN Addressing



| VLAN | Department | Network | Default Gateway | Usable Host Range | Broadcast |

|---|---|---|---|---|---|

| 10 | Management | `192.168.38.0/27` | `192.168.38.1` | `192.168.38.1 – 192.168.38.30` | `192.168.38.31` |

| 20 | HR | `192.168.38.32/27` | `192.168.38.33` | `192.168.38.33 – 192.168.38.62` | `192.168.38.63` |

| 30 | Finance | `192.168.38.64/27` | `192.168.38.65` | `192.168.38.65 – 192.168.38.94` | `192.168.38.95` |

| 40 | Procurement | `192.168.38.96/27` | `192.168.38.97` | `192.168.38.97 – 192.168.38.126` | `192.168.38.127` |

| 50 | Engineering | `192.168.38.128/27` | `192.168.38.129` | `192.168.38.129 – 192.168.38.158` | `192.168.38.159` |

| 60 | Health \& Safety | `192.168.38.160/27` | `192.168.38.161` | `192.168.38.161 – 192.168.38.190` | `192.168.38.191` |

| 70 | Guest Wi-Fi | `192.168.38.192/27` | `192.168.38.193` | `192.168.38.193 – 192.168.38.222` | `192.168.38.223` |



\## Reserved Address Space



The remaining `/27` subnet is reserved for future expansion:



| Purpose | Network | Usable Host Range | Broadcast |

|---|---|---|---|

| Future Branch Office | `192.168.38.224/27` | `192.168.38.225 – 192.168.38.254` | `192.168.38.255` |



This reserved subnet provides capacity for the planned future branch office without requiring the existing departmental addressing scheme to be redesigned.



\## DHCP



DHCP services are provided by the Cisco 3560 multilayer switch.



Each active VLAN has a dedicated DHCP pool providing:



\- IP address

\- Subnet mask

\- Default gateway

\- DNS server



The configured DNS server is:



`8.8.8.8`





