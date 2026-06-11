# Enterprise MSP Stack Architecture

## Executive Summary

This project simulates a modern Managed Service Provider (MSP) operational environment.

The platform provides:

- Identity Services
- Infrastructure Monitoring
- Security Monitoring
- Documentation Management
- Infrastructure Automation
- Backup and Disaster Recovery

The architecture follows enterprise design principles while remaining deployable in a lab environment.

---

## Business Drivers

- Demonstrate Solution Architect capabilities
- Demonstrate enterprise infrastructure design
- Demonstrate operational maturity
- Demonstrate security-first architecture
- Demonstrate automation and Infrastructure as Code

---

## Functional Requirements

### Identity

- Active Directory
- DNS
- DHCP
- Group Policy
- Certificate Services
- Entra ID Integration

### Monitoring

- Infrastructure Monitoring
- Availability Monitoring
- Alerting

### Security

- Endpoint Monitoring
- Log Collection
- Threat Detection

### Documentation

- Knowledge Base
- SOP Repository
- Architecture Repository

### Automation

- PowerShell
- Ansible

### Backup

- Backup Jobs
- Recovery Procedures

---

## Non-Functional Requirements

### Availability

Target: 99.9%

### Security

Least Privilege
Zero Trust Principles

### Scalability

Support:

- 5 customers
- 500 endpoints
- 50 servers

### Maintainability

Documented and repeatable deployments

---

## High-Level Components

### Core Infrastructure

- Proxmox VE
- Ubuntu Server
- Windows Server

### Identity

- Active Directory
- DNS
- DHCP
- ADCS
- Entra ID

### Monitoring

- Zabbix
- Grafana
- Uptime Kuma

### Security

- Wazuh

### Documentation

- BookStack
- NetBox

### Automation

- PowerShell
- Ansible

### Backup

- Restic
