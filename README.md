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
  

Cisco Packet Tracer is used to simulate and test the proposed network.

Basic Device Configuration

Typical configurations include:

enable
configure terminal

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

 # IP ADDRESING PLAN
  Addressing block: 192.168.0/24
 
