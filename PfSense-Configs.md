# PfSense Configurations

> Below will document all the changes and setup for PfSense

## Tips:

- Rules to match port forwards, forwards to show pass instead of link
- Don't forward HTTP or port 80 until the default pfsense web app is listening on a different port
- NAT reflection should be set to **Nat + Proxy**


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
| 80   | 192.168.15.252 | IIS WebServer | Intranet Web Server HTTP |
| 443   | 192.168.15.252 | IIS WebServer | Intranet Web Server HTTPS |
