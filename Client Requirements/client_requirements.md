\# Client Requirements



\## Client Information



| Requirement | Details |

|---|---|

| Client | Reata Construction Group |

| Client ID | CLI-076 |

| Industry | Construction |

| Location | Potchefstroom |

| Network Address Block | `192.168.38.0/24` |





\### 2. IP Addressing



The network must use the allocated `192.168.38.0/24` address block.



The addressing scheme must provide sufficient IP addresses for the six departments and Guest Wi-Fi while allowing for future expansion.



\### 3. DHCP



The network must provide automatic IP address allocation to departmental and Guest Wi-Fi devices.



DHCP should provide:



\- IP address

\- Subnet mask

\- Default gateway

\- DNS server



\### 4. Inter-VLAN Routing



The network must allow controlled communication between VLANs where required.



A multilayer switch will provide Layer 3 functionality and serve as the default gateway for the VLANs.



\### 5. Guest Wi-Fi



Guest devices must be prevented from accessing internal departmental networks.



\### 6. Security and ACLs



Access Control Lists (ACLs) must be implemented to control traffic between network segments.



The Guest VLAN must not be permitted to access internal departmental VLANs.



\### 7. Future Expansion



The addressing plan must allow for a possible branch office within approximately 18 months.



A portion of the available address space should therefore remain available for future expansion.



\### 8. Change Request – Secure Remote Management



One off-site administrator requires secure remote management access to network devices.



SSH must therefore be used for secure management access rather than Telnet.



\## Technical Challenge



The main technical challenge identified for the project is implementing traffic filtering using ACLs while maintaining required network connectivity.





