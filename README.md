# Network Plan for Group 2

A repository setup to document and record the plans ,implementation and development of a complex Network.
This Schema includes two networks, a public network and a private subnet.
The Domain of the network is: **group2.network**

![](https://media.giphy.com/media/n6mEMqAuYOQ8l8qcEE/giphy.gif?cid=790b761193f21ff8db6c0d4c2aafad33dd29979fba85996e&rid=giphy.gif&ct=g)

## Table of Contents

- [Network Plan for Group 2](#network-plan-for-group-2)
  - [Table of Contents](#table-of-contents)
  - [Status and Updates](#status-and-updates)
  - [Tasks and Objectives](#tasks-and-objectives)
  - [Public Network IP Schema](#public-network-ip-schema)
  - [Subnet IP Schema](#subnet-ip-schema)
  - [Hardware Specifications](#hardware-specifications)
  - [Services](#services)
  - [Network Diagram](#network-diagram)
  - [PfSense Configurations](#pfsense-configurations)
    - [Tips](#tips)
    - [Network, IP Address and Gateway](#network-ip-address-and-gateway)
    - [Port Forwarding Rules](#port-forwarding-rules)

---

## Status and Updates

Within this section, the status of the network and updates will be tracked weekly.

Date: **01 / 09 / 2021**
> Created this table

---

## Tasks and Objectives

This section covers tasks and objectives yet to be achieved towards the completion of the network plan

| #          | Task |
| ---------- | ------ |
| **S** | **Stage One** |
| 1 | ~~Plan network requirements, hardware, software~~ |
| 2 | ~~Investigate solutions for proposed network~~ |
| 3 | ~~Design network diagram, including IP address schema~~ |
| 4 | ~~Setup, install and configure ESXi server x 2~~ |
| 5 | ~~Setup and test connectivity within the network~~ |
| 6 | ~~Setup two Domain Controller VM's DC, DNS~~ |
| 7 | ~~Setup, install and configure Linux Webserver~~ |
| 8 | ~~Setup Router for main network~~ |
| 9 | ~~Configure Remote access into network~~ |
| **S2** | **Stage Two** |
| 1 | ~~Re-design network diagram~~ |
| 2 | ~~Investigate VLAN and IP Subnetting~~ |
| 3 | ~~Implement a private network within the main network~~ |
| 4 | ~~Host a virtual IIS webserver in the private network~~ |
| 5 | ~~Host a secure Windows File Server in the private network~~ |
| 6 | ~~Consider Clustering?~~ |
| 7 | ~~Setup network inventory solution~~ |
| 8 | Plan and implement Email Server |
| 9 | ~~Develop security implementation plan~~ |
| 10 | ~~Harden network security~~ |
| 11 | Perform security audit on network |
| 12 | Create a security network diagram |

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
| 192.168.15.120 | Wireless Router | 192.168.15.0/25 | Wi-Fi |
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
| MariaDB  | 3306 | 192.168.15.123 | DB for Password Manager |
| Passbolt | 81   | 192.168.15.123 | Password Manager HTTP/s UI NGINX |

---

## Network Diagram

![Group 2 Network Plan, security colour update border-less](/Network.png)

## PfSense Configurations

> Below will document all the changes and setup for PfSense

---

### Tips

- Rules to match port forwards, forwards to show pass instead of link
- Don't forward HTTP or port 80 until the default PfSense web app is listening on a different port
- NAT reflection should be set to **Nat + Proxy**

---

### Network, IP Address and Gateway

**Router one, main router, Public:**
| Network | IP Address | Range  | Gateway | CIDR |
| ------- | ---------- | ------- | ----- | ---- |
| 192.168.15.0 | 192.168.15.126 | .0 - .127 | 172.20.28.x | /25 |

**Router Two, Subnet-One Router, Private:**
| Network | IP Address | Range | Gateway | CIDR |
| ------- | ---------- | ----- | ------- | ---- |
| 192.168.15.128 | 192.168.15.254 | .128 - .254| 192.168.15.122 | /27 |

---

### Port Forwarding Rules

> **Main Router, Public**

| Port | Service | IP Address | Device | Protocol | Description | Source/Destination |
| ---- | ------- | ---------- | ------ | -------- | ----------- | ------------------ |
| 80   | HTTP  | 192.168.15.122 | Ubuntu Web Server | TCP/UDP | Public Web Server | WAN to LAN |
| 443  | HTTPS | 192.168.15.122 | Ubuntu Web Server | TCP/UDP | Public Web Server | WAN to LAN |

> **Subnet-One Router, Private**

| Port | Service | IP Address | Device | Protocol | Description | Source/Destination |
| ---- | ------- | ---------- | ------ | -------- | ----------- | ------------------ |
| 80   | HTTP  | 192.168.15.252 | IIS WebServer | TCP/UDP | Intranet Web Server HTTP | WAN to LAN |
| 443  | HTTPS | 192.168.15.252 | IIS WebServer | TCP/UDP | Intranet Web Server HTTPS | WAN to LAN |
| 123  | W32Time   | 192.168.15.225-226 | Domain Controller One-Two | UDP | W32 Time | WAN to LAN |
| 135  | DCE   | 192.168.15.225-226 | Domain Controller One-Two | TCP/UDP | DC Operations | WAN to LAN |
| 389  | LDAP  | 192.168.15.225-226 | Domain Controller One-Two | UDP | Lightw Directory Service | WAN to LAN |
| 464  | Kerb   | 192.168.15.225-226 | Domain Controller One-Two | TCP/UDP | Kerberos | WAN to LAN |
| 53   | DNS   | 192.168.15.225-226 | Domain Controller One-Two | TCP/UDP |DNS | WAN to LAN |
| 88  | Kerb Auth | 192.168.15.225-226 | Domain Controller One-Two | UDP | Kerberos Authe | WAN to LAN |
| 138  | FRS   | 192.168.15.225-226 | Domain Controller One-Two | TCP | File Replication | WAN to LAN |
| 139  | FRS   | 192.168.15.225-226 | Domain Controller One-Two | TCP | Replication | WAN to LAN |
| 445  | SMB   | 192.168.15.225-226 | Domain Controller One-Two | TCP | Server msg blk | WAN to LAN |
| 636  | LDAP SSL   | 192.168.15.225-226 | Domain Controller One-Two | TCP | SSL layer LDAP| WAN to LAN |
| 1024  | FRS RPC   | 192.168.15.225-226 | Domain Controller One-Two | TCP/UDP | FRS RPC | WAN to LAN |
| 3296  | LDAP GC   | 192.168.15.225-226 | Domain Controller One-Two | TCP/UDP | LDAP GC | WAN to LAN |
