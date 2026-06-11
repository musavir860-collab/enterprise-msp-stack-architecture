
# Environment Overview


## Hypervisor
| Item           | Value                 |
| -------------- | --------------------- |
| Platform       | Proxmox VE            |
| Cluster        | Single Node (Phase 1) |
| Expansion      | 3-Node Cluster        |
| Storage        | Local SSD             |
| Backup Storage | Separate Repository   |


## Virtual Machine Inventory
| VM                | Hostname | OS                  | vCPU | RAM  | Disk   |
| ----------------- | -------- | ------------------- | ---- | ---- | ------ |
| Domain Controller | DC01     | Windows Server 2025 | 2    | 4 GB | 80 GB  |
| Operations Server | OPS01    | Ubuntu 24.04        | 4    | 8 GB | 100 GB  |
| Monitoring        | MON01    | Ubuntu 24.04        | 4    | 8 GB | 100 GB |
| Security          | SEC01    | Ubuntu 24.04        | 4    | 8 GB | 150 GB |
| Backup            | BAK01    | Ubuntu 24.04        | 2    | 4 GB | 100 GB |

## Container Services

## MON01
| Service     |
| ----------- |
| Zabbix      |
| Grafana     |
| Uptime Kuma |


## SEC01
| Service         |
| --------------- |
| Wazuh Manager   |
| Wazuh Dashboard |
| Wazuh Indexer   |

## OPS01
| Service            |
| ------------------ |
| Ansible            |
| Git                |
| NetBox             |
| BookStack          |
| Automation Scripts |



## Network Assignment
## Management VLAN
VLAN 10
10.10.10.0/24


| Device  | IP          |
| ------- | ----------- |
| Proxmox | 10.10.10.10 |
| MGMT01  | 10.10.10.20 |


## Server VLAN
VLAN 20
10.10.20.0/24

| Device | IP          |
| ------ | ----------- |
| DC01   | 10.10.20.10 |
| DOCS01 | 10.10.20.20 |
| MON01  | 10.10.20.30 |
| SEC01  | 10.10.20.40 |
| BAK01  | 10.10.20.50 |


## DNS Design

### Internal Zone
empire.local

### Records
dc01.empire.local
docs01.empire.local
mon01.empire.local
sec01.empire.local
bak01.empire.local
mgmt01.empire.local


## Service URLs
Later through reverse proxy:
https://wiki.empire.local
https://netbox.empire.local
https://zabbix.empire.local
https://grafana.empire.local
https://wazuh.empire.local
https://kuma.empire.local

## Active Directory Design

### Create:
Forest:
empire.local

### OU Structure:
Empire
├── Users
├── Groups
├── Servers
├── Workstations
├── Service Accounts
├── Admin Accounts
└── Test Lab


## Service Accounts

### Create planned accounts:
svc_zabbix
svc_wazuh
svc_backup
svc_ansible
svc_monitoring


## Backup Policy
| System            | Frequency |
| ----------------- | --------- |
| Domain Controller | Daily     |
| Monitoring        | Daily     |
| Security          | Daily     |
| Documentation     | Daily     |
| Automation        | Daily     |

### Retention:
Daily: 30 Days
Weekly: 12 Weeks
Monthly: 12 Months


