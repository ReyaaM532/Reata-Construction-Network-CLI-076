# Network Testing

Testing was conducted in Cisco Packet Tracer to verify DHCP address allocation and connectivity between departmental PCs and their respective VLAN gateways.

## Departmental DHCP and Connectivity Testing

Each departmental PC was configured to obtain its IP address automatically using DHCP from the Cisco 3560 multilayer switch. The assigned IP address, subnet mask, default gateway, and connectivity to the VLAN gateway were verified.

| Test | VLAN | Expected Gateway | Result |
|------|------|------------------|--------|
| Management | 10 | `192.168.38.1` | Passed |
| HR | 20 | `192.168.38.33` | Passed |
| Finance | 30 | `192.168.38.65` | Passed |
| Procurement | 40 | `192.168.38.97` | Passed |
| Engineering | 50 | `192.168.38.129` | Passed |
| Health & Safety | 60 | `192.168.38.161` | Passed |

### Evidence

The following screenshots provide evidence of the DHCP and connectivity tests:

- `01_Management_DHCP_Connectivity.png`
- `02_HR_DHCP_Connectivity.png`
- `03_Finance_DHCP_Connectivity.png`
- `04_Procurement_DHCP_Connectivity.png`
- `05_Engineering_DHCP_Connectivity.png`
- `06_Health_Safety_DHCP_Connectivity.png`

Each screenshot shows the PC's automatically assigned network configuration and successful connectivity to its respective VLAN gateway.

## Guest Wi-Fi DHCP Testing

The Guest Wi-Fi laptop was configured to obtain its IP address automatically using DHCP from the Guest VLAN.

The Guest DHCP configuration was verified as:

- Guest VLAN: 70
- Guest subnet: `192.168.38.192/27`
- Default gateway: `192.168.38.193`
- DNS server: `8.8.8.8`

The Guest laptop initially failed to obtain an IP address because the Guest ACL did not permit DHCP client requests. After adding the DHCP permit statement to the ACL, the laptop successfully obtained an IP address from the Guest subnet.

### Guest DHCP Evidence

- `01_Guest_DHCP_Failure.png` — Initial DHCP failure and APIPA address.
- `02_Guest_DHCP_Success.png` — Successful DHCP address allocation after the ACL correction.

## Testing Still to Be Completed

The following network functions will be tested and documented separately:

- Guest Wi-Fi ACL restrictions
- SSH remote management