# Network Plan for Group 2

A repository setup to document and record the plans ,implementation and development of a complex Network.
This Schema includes two networks, a public network and a private subnet.
The Domain of the network is: **group2.network**

## Table of Contents

- [Network Plan for Group 2](#network-plan-for-group-2)
  - [Table of Contents](#table-of-contents)
  - [Public Network IP Schema](#public-network-ip-schema)
  - [Subnet IP Schema](#subnet-ip-schema)
  - [Hardware Specifications](#hardware-specifications)
  - [Services](#services)
  - [Network Diagram](#network-diagram)

---

## Public Network IP Schema

| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.15.0 <=> 192.168.15.127 | 192.168.15.126 | 255.255.255.128 | /25 |

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| 192.168.15.1 | ESXi 6.7| 192.168.15.0/25 | Virtual Host 1|
| 192.168.15.2 | ESXi 6.7| 192.168.15.0/25  | Virtual Host 2|
| 192.168.15.3    | Windows 10 Terminal    | 192.168.15.0/25 | Andrew |
| 192.168.15.4    | Linux Fedora Terminal  | 192.168.15.0/25 | Corey |
| 192.168.15.5    | Windows 10 Terminal    | 192.168.15.0/25 | Reece |
| 192.168.15.6    | Windows 10 Terminal    | 192.168.15.0/25 | Jeremiah |
| 192.168.15.121  | Windows Server Email Server | 192.168.15.0/25 | HMail internal |
| 192.168.15.122  | Router  | 192.168.15.0/25 | Router for 224 Subnet |
| 192.168.15.123  | Ubuntu-Server    | 192.168.15.0/25 |  Apache Web Server |
| 192.168.15.124  | Switch  | 192.168.15.0/25 | Distribution Switch |
| 192.168.15.125  | Switch  | 192.168.15.0/25 | Main Switch |
| 192.168.15.126  | Network | 192.168.15.0/25 | Main Router |

---

## Subnet IP Schema

| Main Network Range | Gateway | NetMask | CIDR |
| --------------------------------- | -------------- | --------------- | --- |
| 192.168.15.224 <=> 192.168.15.255 | 192.168.15.254 | 255.255.255.224 | /27 |

| IP Address     | Device                 | Network            | Description         |
| -------------- | ---------------------- | ------------------ | ------------------- |
| 192.168.15.225 | Domain Controller 1    | 192.168.15.224/27  | Windows Server 2016 |
| 192.168.15.226 | Domain Controller 2    | 192.168.15.224/27  | Windows Server 2016 |
| 192.168.15.228 | Ubuntu Desktop         | 192.168.15.224/27  | Terminal            |
| 192.168.15.229 | Windows Server         | 192.168.15.224/27  | File Server         |
| 192.168.15.252 | IIS Web Server         | 192.168.15.224/27  | Windows Server 2016 |
| 192.168.15.253 | Switch                 | 192.168.15.224/27  | Virtual Switch 1    |
| 192.168.15.254 | Network                | 192.168.15.224/27  | Virtual Router 1    |

## Hardware Specifications

| Device   | Specifications   | Role | Quantity |
| ---------| ---------------- | -------- | -----|
| Dell R520 | Ram: 26 GB Storage: yes  | DC2 | 1x |
| Dell R720 | Ram: 16 GB Storage: yes   | DC1 | 1x |
| Dell R230 | Ram: 16 GB Storage: 1.4 TB | WebServer | 1x |
| iMac | N/A | Terminal | 4x |
| Router | N/A | Router | 1x |
| Cisco Switch 2801 | N/A | Switch | 1x |

---

## Services

| Service  | Port | Ip Address | Description |
| -------- | ---- | ---------- | ----------- |
| MariaDB  | 3306 | 192.168.15.124 | DB for Password Manager |
| Passbolt | 81   | 192.168.15.124 | Password Manager HTTP/s UI NGINX |

---

## Network Diagram

![Complex diagram - bottom window re-edit](https://user-images.githubusercontent.com/89438022/130699074-09577e77-6bb0-4430-b4ee-5a29bb9b114d.jpg)