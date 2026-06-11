# Step 1 — Proxmox Foundation

## Network Bridges
| Network Bridge | Purpose      |
| -------------- | ------------ |
| vmbr0          | Management   |
| vmbr20         | Servers      |
| vmbr30         | Workstations |
| vmbr40         | Monitoring   |
| vmbr50         | DMZ          |
| vmbr60         | Backup       |

## Storage
| Storage Pool  | Type / Purpose |
| ------------- | -------------- |
| local         | Local          |
| local-lvm     | Local-LVM      |
| backup-storage| Backup Storage |

## Naming Standard
| Host / VM Name | Role / Function       |
| -------------- | --------------------- |
| PVE01          | Proxmox VE Host 01    |
| DC01           | Domain Controller 01  |
| OPS01          | Operations 01         |
| MON01          | Monitoring 01         |
| SEC01          | Security 01           |
| BAK01          | Backup 01             |


## Step 2 — Identity Platform
**Host:** DC01  
**OS:** Windows Server 2025  
**Domain:** `empire.local`

| Deployment Phase | Task / Configuration | Details / Requirements |
| ---------------- | -------------------- | ---------------------- |
| **Initial Setup**| Install OS           | Windows Server 2025    |
|                  | Network Config       | Configure Static IP    |
|                  | Hostname             | Rename Host to DC01    |
| **Roles** | Identity             | AD DS                  |
|                  | Name Resolution      | DNS                    |
|                  | IP Assignment        | DHCP                   |
|                  | Certificate Authority| ADCS                   |
| **Domain Setup** | Active Directory     | Create domain: `empire.local` |
| **Configuration**| Directory Structure  | OU Structure           |
|                  | Identity Security    | Service Accounts       |
|                  | Access Control       | Groups                 |
|                  | Policy Enforcement   | GPO Baseline           |

---

## Step 3 — Operations Platform
**Host:** OPS01  
**OS:** Ubuntu 24.04 LTS  
**Role:** MSP Operations Hub

| Component Type | Software / Tool | Function |
| -------------- | --------------- | -------- |
| **OS / Runtime**| Ubuntu 24.04 LTS| Base Operating System |
| **Containers** | Docker          | Container Runtime |
|                 | Docker Compose  | Multi-Container Orchestration |
| **Automation** | Git             | Version Control |
|                 | Ansible         | Configuration Management |
| **Proxy** | Nginx Proxy Manager | Reverse Proxy & SSL Management |
| **Apps & Data** | BookStack       | Documentation & Knowledge Base |
|                 | NetBox          | IPAM & DCIM (Source of Truth) |

---

## Step 4 — Monitoring Platform
**Host:** MON01  
*Architectural Principle: Observe → Then Protect (Monitoring precedes security)*

| Component Type | Software / Tool | Function |
| -------------- | --------------- | -------- |
| **Runtime** | Docker          | Container Runtime |
|                 | Docker Compose  | Deployment Orchestration |
| **Stack** | Zabbix          | Infrastructure & Endpoint Monitoring |
|                 | Grafana         | Data Visualization & Dashboards |
|                 | Uptime Kuma     | Service Availability & Uptime Alerts |

---

## Step 5 — Security Platform
**Host:** SEC01  

| Component Type | SIEM / XDR Component | Target Agent Connections |
| -------------- | -------------------- | ------------------------ |
| **Core Stack** | Wazuh Indexer        | Monitored via Agent      |
|                 | Wazuh Manager        | Monitored via Agent      |
|                 | Wazuh Dashboard      | Monitored via Agent      |
| **Agents** | DC01                 | Active Endpoint Agent    |
|                 | OPS01                | Active Endpoint Agent    |
|                 | MON01                | Active Endpoint Agent    |
|                 | BAK01                | Active Endpoint Agent    |

---

## Step 6 — Backup Platform
**Host:** BAK01  

| Backup Component | Software / Protocol | Target Systems to Backup |
| ---------------- | ------------------- | ------------------------ |
| **Engine** | Restic              | Orchestrates backups     |
| **Storage** | NFS Repository      | Backup Destination Target|
| **Targets** | DC01                | Identity Backup          |
|                  | OPS01               | Operations Backup        |
|                  | MON01               | Monitoring Backup        |
|                  | SEC01               | Security Backup          |
