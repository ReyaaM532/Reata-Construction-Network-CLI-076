# Reata-Construction-Network-CLI-076
 This project present a computer network that handles ACLs (traffic filtering policy) of a Reata Construction Group and allows for client change request of allowing one off-site administrator secure remote management access to network devices. In addition, the addressing plan allow's for a branch office that may be opened within 18 months. The network will be designed and tested in Cisco Packet Tracer

# Client Background
 Client ID: CLI-076
 
 Organisation:Reata Construction Group (Potchefstroom)
 
 Industry: Construction
 
 Technical Challenge: ACLs (traffic filtering policy)
 
 Constraint: A branch office may be opened within 18 months
 
 Change Request: CR9: One off-site administrator requires secure remote management access to network devices

 # Prerequisites
  Cisco Packet Tracer
  



Typical configurations include:

enable
configure t

hostname COMPANY-RTR

enable secret <password>

service password-encryption

banner motd #UNAUTHORISED ACCESS PROHIBITED#

line console 0
password <password>
login

line vty 0 4
password <password>
login
transport input ssh

 ## IP ADDRESING PLAN and VLAN Configuration
  Addressing block: 192.168.0/24


  

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
 
