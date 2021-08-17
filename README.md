# Network-Plan-Group2
Repo setup for deocumentation and record of plans and implementation

## Network IP Schema

>#### Shows the general IP schema of the network.

> **192.168.15.0 => 192.168.15.127 Gateway == 192.168.15.126 NetMask == 255.255.255.128 /25**

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| 192.168.15.1 | ESXi 6.7| 192.168.15.0/25 | Virtual Host 1|
| 192.168.15.2 | ESXi 6.7| 192.168.15.0/25  | Virtual Host 2|
| 192.168.15.3    | Windows 10 Terminal    | 192.168.15.0/25 | Andrew |
| 192.168.15.4    | Linux Fedora Terminal  | 192.168.15.0/25 | Corey |
| 192.168.15.5    | Windows 10 Terminal    | 192.168.15.0/25 | Reece |
| 192.168.15.6    | Windows 10 Terminal    | 192.168.15.0/25 | Jeremiah |
| 192.168.15.122  | Router  | 192.168.15.0/25 | Router for 224 Subnet |
| 192.168.15.123  | Ubuntu-Server    | 192.168.15.0/25 |  Apache Web Server |
| 192.168.15.124  | Switch  | 192.168.15.0/25 | Distribution Switch |
| 192.168.15.125  | Switch  | 192.168.15.0/25 | Main Switch |
| 192.168.15.126  | Network | 192.168.15.0/25 | Main Router |


## Subnet Range:
> **192.168.15.224 => 192.168.15.255 Gateway == 192.168.15.254 Netmask == 255.255.255.224 /27**

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| 192.168.15.225 | Domain Controller 1    | 192.168.15.224/27  | Windows Server 2016|
| 192.168.15.226 | Domain Contorller 2    | 192.168.15.224/27  | Windows Server 2016|
| 192.168.15.227 | Windows Server | 192.168.15.224/27 | File Server |
| 192.168.15.252 | IIS Web Server    | 192.168.15.224/27  | Windows Server 2016|
| 192.168.15.253 | Switch  | 192.168.15.224/27 | Virtual Switch 1|
| 192.168.15.254 | Network | 192.168.15.224/27 | Virtual Router 1|

## Hardware Specifications

| Device   | Specifications   | Role | Quantity |
| ---------| ---------------- | -------- | -----|
| Dell R520 | Ram: 26 GB Storage: yes  | DC2 | 1x |
| Dell R720 | Ram: 16 GB Storage: yes   | DC1 | 1x |
| Dell R230 | Ram: 16 GB Storage: 1.4 TB | WebServer | 1x |
| iMac | N/A | Terminal | 4x |
| Router | N/A | Router | 1x |
| Cisco Switch 2801 | N/A | Switch | 1x |
## Network Diagram:
<img src='./Network.png'></img>
