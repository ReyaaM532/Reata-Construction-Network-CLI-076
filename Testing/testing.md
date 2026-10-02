# Network Testing

Testing was conducted in Cisco Packet Tracer to verify DHCP address allocation, VLAN gateway connectivity, Guest Wi-Fi access restrictions, and SSH remote management access.

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

The Guest laptop initially failed to obtain an IP address because the Guest ACL did not explicitly permit DHCP client requests. After adding the DHCP permit statement to the ACL, the laptop successfully obtained an IP address from the Guest subnet.

### Guest DHCP Evidence

- `GuestLaptop_DHCP_Failure.png` — Initial DHCP failure and APIPA address.
- `GuestLaptop_DHCP_Success.png` — Successful DHCP address allocation after the ACL correction.

## Guest Wi-Fi ACL Testing

The Guest Wi-Fi ACL was tested to verify that Guest devices could reach their own VLAN gateway while being prevented from accessing internal departmental VLANs.

The Guest laptop successfully reached its own gateway:

`192.168.38.193`

The Guest laptop was unable to reach the internal departmental VLAN gateways:

- `192.168.38.1` — Management
- `192.168.38.33` — HR
- `192.168.38.65` — Finance
- `192.168.38.97` — Procurement
- `192.168.38.129` — Engineering
- `192.168.38.161` — Health & Safety

### Guest ACL Evidence

- `03_Guest_ACL_Management_Block.png` — Guest laptop was prevented from accessing the Management VLAN gateway.
- `04_Guest_ACL_HR_Finance_Block.png` — Guest laptop was prevented from accessing the HR and Finance VLAN gateways.
- `05_Guest_ACL_Procurement_Engineering_Block.png` — Guest laptop was prevented from accessing the Procurement and Engineering VLAN gateways.
- `06_Guest_ACL_Gateway_Access.png` — Guest laptop successfully reached its own Guest VLAN gateway.

## SSH Remote Management Testing

SSH remote management was tested from the Management PC on VLAN 10 to the Cisco 3560 multilayer switch.

The Management PC successfully reached the switch gateway at:

`192.168.38.1`

SSH access was then tested using:

```text
ssh -l admin 192.168.38.1
```

The login was successful and provided access to the switch CLI.

### SSH Evidence

- `SSH_Testing_Management.png` — Successful SSH login from the Management PC to the Cisco 3560 multilayer switch.