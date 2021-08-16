img# Network-Plan-Group2
Repo setup for deocumentation and record of plans and implementation

# Network IP Schema

> Shows the general IP schema of the network.

> **192.168.15.0 => 192.168.15.127**

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| 192.168.15.1   | Windows 10 Terminal    | 192.168.15.0/25 | Andrew |
| 192.168.15.2   | Linux Fedora Terminal  | 192.168.15.0/25 | Corey |
| 192.168.15.3  | Windows 10 Terminal    | 192.168.15.0/25 | Reece |
| 192.168.15.4  | Windows 10 Terminal    | 192.168.15.0/25 | Jeremiah |
| 192.168.15.126  | Switch  | 192.168.15.0/25 | Main Switch |
| 192.168.15.127 | Network | 192.168.15.0/25 | Main Router |


## Subnet Range:
> **192.168.15.224 => 192.168.15.255**

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| 192.168.15.225 | Domain Controller 1    | 192.168.15.224/27  | Windows Server 2016|
| 192.168.15.226 | Domain Contorller 2    | 192.168.15.224/27  | Windows Server 2016|
| 192.168.15.227 | ESXi 6.0| 192.168.15.224/27 | Virtual Host 1|
| 192.168.15.228 | ESXi 7.0| 192.168.15.224/27  | Virtual Host 2|
| 192.168.15.251  | Ubuntu-Server    | 192.168.15.224/27  |  Apache Web Server |
| 192.168.15.252 | IIS Web Server    | 192.168.15.224/27  | Windows Server 2016|
| 192.168.15.253 | Switch  | 192.168.15.224/27 | Virtual Switch 1|
| 192.168.15.254 | Network | 192.168.15.224/27 | Virtual Router 1|

# Hardware Specifications

| Device   | Specifications   | Role | Quantity |
| ---------| ---------------- | -------- | -----|
| Dell R520 | Ram: 26 GB Storage: yes  | DC2 | 1x
| Dell R720 | Ram: 16 GB Storage: yes   | DC1 | 1x
| Dell R230 | Ram: 16 GB Storage: 1.4 TB | WebServer | 1x
| iMac | N/A | Terminal | 4x

# Network Diagram:
<img src='./Network.png'></img>