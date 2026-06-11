| VLAN | Name         | Purpose                  |
| ---- | ------------ | ------------------------ |
| 10   | Management   | Hypervisors & Management |
| 20   | Servers      | Infrastructure Servers   |
| 30   | Workstations | Client Devices           |
| 40   | Monitoring   | Zabbix/Wazuh             |
| 50   | DMZ          | Public Services          |
| 60   | Backup       | Backup Traffic           |
| 70   | Kubernetes   | Future Expansion         |
| 99   | Transit      | Routing                  |

10.10.10.0/24  Management
10.10.20.0/24  Servers
10.10.30.0/24  Workstations
10.10.40.0/24  Monitoring
10.10.50.0/24  DMZ
10.10.60.0/24  Backup
10.10.70.0/24  Kubernetes
