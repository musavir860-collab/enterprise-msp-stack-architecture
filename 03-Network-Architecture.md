| VLAN | Name           | Subnet        | Purpose                                      |
| ---- | -------------- | ------------- | -------------------------------------------- |
| 10   | Management     | 10.10.10.0/24 | Proxmox, switches, infrastructure management |
| 20   | Infrastructure | 10.10.20.0/24 | AD, DNS, DHCP, BookStack, NetBox             |
| 30   | User Devices   | 10.10.30.0/24 | Windows clients                              |
| 40   | Monitoring     | 10.10.40.0/24 | Zabbix, Grafana                              |
| 50   | Security       | 10.10.50.0/24 | Wazuh, Security tools                        |
| 60   | Backup         | 10.10.60.0/24 | Backup repositories                          |
| 70   | DMZ            | 10.10.70.0/24 | Public-facing applications                   |
| 80   | Kubernetes     | 10.10.80.0/24 | Future K3s cluster                           |
| 99   | Transit        | 10.10.99.0/24 | Router/firewall transit                      |
