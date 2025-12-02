# Network-topology-edu
A Cisco Packet Tracer network simulation of an English Department building, featuring VLANs, routing, and connectivity for PCs, laptops, printers, and IP phones with both wired and wireless technologies.

The topology provides reliable connectivity within the department and ensures flexibility by incorporating both **wired and wireless technologies**.


## 🛠 Software Used
- Cisco Packet Tracer

## 🔹 Features
- Designed and implemented VLANs for network segmentation
- Configured routing between different networks
- Ensured connectivity for multiple device types (PCs, printers, laptops, IP phones)
- Combined wired and wireless connections for flexibility
- Simulated network traffic and tested performance

## 🖥 Router IP Address Table

| Device      | Interface      | IP Address       | Subnet Mask     | Default Gateway |
|------------|---------------|----------------|----------------|----------------|
| Router1    | Fa0/0         | 192.168.1.1    | 255.255.255.0  | N/A            |
|            | Se0/1/0       | 11.0.0.1       | 255.0.0.0      | N/A            |
|            | Se0/1/1       | 13.0.0.2       | 255.0.0.0      | N/A            |
| Router2    | Fa0/0         | 192.168.3.1    | 255.255.255.0  | N/A            |
|            | Fa0/1         | 192.168.4.1    | 255.255.255.0  | N/A            |
|            | Se0/1/0       | 12.0.0.2       | 255.0.0.0      | N/A            |
| Router0    | Fa0/0         | 192.168.2.1    | 255.255.255.0  | N/A            |
|            | Se0/1/0       | 11.0.0.2       | 255.0.0.0      | N/A            |
|            | Se0/1/1       | 12.0.0.1       | 255.0.0.0      | N/A            |
| Router4    | Fa0/0         | 192.168.5.1    | 255.255.255.0  | N/A            |
|            | Se0/3/0       | 13.0.0.1       | 255.0.0.0      | N/A            |

## 🖥 Switches

| Switch      | Ports / VLAN  | Notes |
|------------|---------------|-------|
| Switch0    | Fa0/1 – Fa0/3 |       |
| Switch1    | Fa0/1 – Fa0/2 |       |
| Switch2    | Fa0/1 – Fa0/2 |       |
| Switch3    | Fa0/1 – Fa0/5 |       |
| Switch4    | Vlan 10, 20   |       |

## 🖥 PC / Laptop / Printer / IP Phone IP Table

| Device      | Interface      | IP Address       | Subnet Mask     | Default Gateway | Notes        |
|------------|---------------|----------------|----------------|----------------|-------------|
| PC0        | NIC           | 192.168.1.2    | 255.255.255.0  | 192.168.1.1    |             |
| PC1        | NIC           | 192.168.1.3    | 255.255.255.0  | 192.168.1.1    |             |
| PC2        | NIC           | 192.168.2.2    | 255.255.255.0  | 192.168.2.1    |             |
| PC3        | NIC           | 192.168.2.3    | 255.255.255.0  | 192.168.2.1    |             |
| PC4        | NIC           | 192.168.3.2    | 255.255.255.0  | 192.168.3.1    |             |
| PC5        | NIC           | 192.168.3.3    | 255.255.255.0  | 192.168.3.1    |             |
| PC6        | Wireless      | 192.168.4.8    | 255.255.255.0  | 192.168.4.1    | DHCP        |
| PC7        | NIC           | 192.168.5.2    | 255.255.255.0  | 192.168.5.1    | DHCP        |
| PC8        | NIC           | 192.168.5.3    | 255.255.255.0  | 192.168.5.1    | DHCP        |
| Laptop0    | NIC           | 192.168.4.3    | 255.255.255.0  | 192.168.4.1    | DHCP        |
| Laptop1    | NIC           | 192.168.4.4    | 255.255.255.0  | 192.168.4.1    |             |
| Laptop3    | Wireless      | 192.168.4.9    | 255.255.255.0  | 192.168.4.1    |             |
| Printer0   | FastEthernet  | 192.168.4.5    | 255.255.255.0  | 192.168.4.1    |             |
| Printer1   | FastEthernet  | 192.168.1.3    | 255.255.255.0  | 192.168.1.1    |             |
| Printer2   | Wireless      | 192.168.4.10   | 255.255.255.0  | 192.168.4.1    | DHCP        |
| Server     | FastEthernet  | 192.168.4.2    | 255.255.255.0  | 192.168.4.1    |             |
| IP Phone0  | FastEthernet  | 192.168.5.2    | 255.255.255.0  | 192.168.5.1    | Line: 0555  |
| IP Phone2  | FastEthernet  | 192.168.5.3    | 255.255.255.0  | 192.168.5.1    | Line: 0555  |



## 🔧 Switch VLAN Configuration Instructions
Follow these steps to configure VLANs and trunking:

1. **Create VLANs**
```bash
Switch> enable
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# name Voice
Switch(config-vlan)# exit
Switch(config)# vlan 20
Switch(config-vlan)# name Data
Switch(config-vlan)# exit

Switch(config)# interface range fa0/2-15
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 20
Switch(config-if-range)# exit


Switch(config)# interface range fa0/2-15
Switch(config-if-range)# switchport voice vlan 10
Switch(config-if-range)# exit

Switch(config)# interface fa0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# exit
