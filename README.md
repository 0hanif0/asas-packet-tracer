# ASAS PACKET TRACER

## Erase the startup configurations and VLANs from the router and switch and reload the devices
1. Router
- en
- erase startup-config
- reload

2. Switch
- en
- erase startup-config
- delete vlan.dat
- relaod

## Configure Router
- en [enable privileged EXEC mode]
- config terminal [enter configuration mode]

1. Disable DNS lookup
- no ip domain lookup

2. Router name
- hostname <>

3. Domain name
- ip domain-name <>

4. Encrypted privileged EXEC password
- enable secret <>

5. Console access password
- line console 0
- password <>
- login
- exit

6. Set the minimun length for passwords
- security password min-length <>

7. Create administrative in local database
- username <> secret <>

8. Set login on vty lines to use local database
- line vty 0 15
- login local

9. Set vty lines to accept SSH connections only
- transport input ssh
- exit

10. Encrypted the clear text passwords
- service password-encryption

11. Configure MOTD Banner
- banner motd "Unauthorized Access is Prohibited!"

12. Enable ipv6 routing
- ipv6 unicast-routing

13. Configure interface G0/0/0
- int g0/0/0 
- description <> [set description]
- ip address 192.168.10.129 255.255.255.192 [set layer 3 ipv4 address]
- ipv6 address fe80::1 link-local [set ipv6 link local address as fe80::1]
- no shutdown [activate int]
- exit

14. Generate RSA crypto key
- crypto key generate rsa general-keys modulus 1024

15. Save the running configuration to startup configuration file
- copy running-config startup-config

16. Set the clock
- clock set 13:30:00 5 March 2023
## Configure Switch
- en [enable privileged EXEC mode]
- config terminal [enter configuration mode]

1. Disable DNS lookup
- no ip domain lookup

2. Switch name
- hostname <>

3. Domain name
- ip domain-name <>

4. Encrypted privileged EXEC password
- enable secret <>

5. Console access password
- line console 0
- password <>
- login
- exit

6. Shutdown unused int f0/1-4
- int range g1/0/1-4
- shutdown
- exit

7. Shutdown unused int f0/7-24
- int range g1/0/7-24
- shutdown
- exit

8. Shutdown unused int g0/1-2
- int range g1/1/1-2
- shutdown
- exit

9. Create administrative in local database
- username <> secret <>

10. Set login on vty lines to use local database
- line vty 0 15
- login local

11. Set vty lines to accept SSH connections only
- transport input ssh
- exit

12. Encrypted the clear text passwords
- service password-encryption

13. Configure MOTD Banner
- banner motd "Unauthorized Access is Prohibited!"

14. Configure vlan 1
- int vlan 1
- description <> [set description]
- ip address 192.168.10.2 255.255.255.128 [set layer 3 ipv4 address]
- ipv6 address fe80::2 link-local [set ipv6 link local address as fe80::2]
- no shutdown [activate int]
- exit

15. Set ip gateway
- ip default-gateway 192.168.10.1

16. Ping PC-B to PC-A S1 VLAN 1
- ipv6 route ::0/ 2001:db8:acad:a ::1

17. Generate RSA crypto key
- crypto key generate rsa general-keys modulus 1024

## Configure PC - A
- ip address : 192.168.10.126
- subnet mask : 255.255.255.128
- default gateway : 192.168.10.1
- dns server : 0.0.0.0
- ipv6 : 2001:db8:acad:a ::a /64
- link local address : default
- ipv6 gateway : fe80::1
- ipv6 DNS server : default

## Configure PC - B
- ip address : 192.168.10.190
- subnet mask : 255.255.255.192
- default gateway : 192.168.10.129
- dns server : 0.0.0.0
- ipv6 : 2001:db8:acad:b ::b /64
- link local address : default
- ipv6 gateway : fe80::1
- ipv6 DNS server : default

## Test and Verify end-to-end Connectivity
- open cmd and ping

## IOS CLI to gather device information
- open terminal for Router
- en
- show version [router model][IOS image file][total RAM][total Flash Memory][configuration Register][CLI COMMAND USED]
- show ip interface brief [display info ipv4 interfaces Router]
- show ip route [display ipv4 routing table]
- show arp [display layer2 to layer3 mapping Router]
- show interface g0/0/0 [display ipv4 interface g0/0/0 Router]
- show ipv6 route [display ipv6 routing table]
- show ipv6 interface brief [display info ipv6 interfaces and status]
- show cdp neighbor [display info device id,local interface,hold time,capability, platform, port id]
- copy running-config startup-config [save current config so it will be used the next time the router is started] IMPORTANT use at router and switch
