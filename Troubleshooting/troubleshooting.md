# Troubleshooting

## Guest Wi-Fi DHCP Failure

### Problem

The Guest Wi-Fi laptop initially failed to obtain an IP address automatically using DHCP. The laptop displayed **"DHCP failed"** and assigned itself an APIPA address in the `169.254.x.x` range.

### Investigation

The DHCP configuration on the Cisco 3560 Multilayer Switch was checked using:

```text
show running-config | section ip dhcp
```

The Guest DHCP pool was confirmed to be correctly configured:

```text
ip dhcp pool GUEST
 network 192.168.38.192 255.255.255.224
 default-router 192.168.38.193
 dns-server 8.8.8.8
```

VLAN 70 was confirmed to be active, and the Guest wireless connection and switchport were also verified.

The Guest ACL was then inspected using:

```text
show access-lists
```

The ACL was applied inbound on VLAN 70 and did not explicitly permit DHCP client requests.

### Cause

The Guest ACL was preventing the Guest laptop's initial DHCP request from passing through the VLAN 70 interface.

### Resolution

A DHCP permit statement was added to the `GUEST_RESTRICTIONS` ACL:

```text
ip access-list extended GUEST_RESTRICTIONS
 permit udp any eq bootpc any eq bootps
```

The existing restrictions preventing Guest Wi-Fi traffic from accessing the internal departmental VLANs were retained.

### Verification

After the DHCP permit statement was added, the Guest laptop was returned to DHCP configuration and successfully received an IP address from the Guest VLAN subnet.

The Guest network configuration was verified to use:

- Guest subnet: `192.168.38.192/27`
- Default gateway: `192.168.38.193`
- DNS server: `8.8.8.8`

The corrected configuration was saved to the 3560 using:

```text
copy running-config startup-config
```

### Evidence

- `01_Guest_DHCP_Failure.png` — Guest laptop showing the initial DHCP failure and APIPA address.
- `02_Guest_DHCP_Success.png` — Guest laptop successfully receiving an IP address through DHCP after the ACL correction.