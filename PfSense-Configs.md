# PfSense Configurations

> Below will document all the changes and setup for PfSense

## Network, IP Address and Gateway
**Router one, main router:**
| Network | IP Address | Range  | Gateway | CIDR |
| ------- | ---------- | ------- | ----- | ---- |
| 192.168.15.0 | 192.168.15.126 | .0 - .127 | 172.20.28.x | /25 |

**Router Two, Subnet-One Router:**
| Network | IP Address | Range | Gateway | CIDR |
| ------- | ---------- | ----- | ------- | ---- |
| 192.168.15.128 | 192.168.15.254 | .128 - .254| 192.168.15.122 | /27 |

## Port Forwarding Rules
> **Main Router** 

| Port | IP Address | Device | Description | 
| ---- | ---------- | ------ | ---------------------------- |
| 80   | 192.168.15.122 | Ubuntu Web Server | External Web Server HTTP |
| 443   | 192.168.15.122 | Ubuntu Web Server | External Web Server HTTPS |

> **Subnet-One Router** 

| Port | IP Address | Device | Description | 
| ---- | ---------- | ------ | ---------------------------- |
| 80   | 192.168.15.122 | Ubuntu Web Server | External Web Server HTTP |
| 443   | 192.168.15.122 | Ubuntu Web Server | External Web Server HTTPS |