# Systems & Security Homelab

A personal lab developed to practice virtualization, VM networking, systems administration, monitoring, and security on dedicated server hardware.

## Project focus

The core learning focus is understanding how Proxmox virtual machines connect through virtual bridges, how OPNsense interfaces relate to those connections, and how to investigate loss of VM or firewall-management access.

[VM networking and OPNsense troubleshooting](docs/vm-networking-opnsense.md)

## Environment overview

| Layer | Previously documented components |
|---|---|
| Hardware | Dell PowerEdge R630, Dell iDRAC, Cisco managed switch, ASUS router |
| Virtualization | Proxmox VE, KVM virtual machines, LXC containers |
| Networking | OPNsense VM, VLANs, switch ACLs, isolated lab subnet |
| Identity | Windows Server 2022, Active Directory, organizational units, Group Policy |
| Infrastructure services | Pi-hole, NGINX Proxy Manager, TrueNAS |
| Backup and monitoring | Proxmox Backup Server, Zabbix, Grafana, Kibana |
| Applications | GitLab, BookStack, Home Assistant, Jellyfin |

## Virtualization and networking

Proxmox hosts full virtual machines and lightweight containers. Managed-switch VLANs and access controls to separate traffic, with an isolated subnet for lab workloads.

The networking work focuses on distinguishing four layers:

1. Physical connections: server NICs, switch ports, and upstream connectivity.
2. Proxmox networking: bridges, attached interfaces, and VM network adapters.
3. Guest configuration: assigned interfaces, addresses, masks, and routes.
4. Access controls: relevant VLAN configuration and firewall rules.

OPNsense was operating as a virtualized firewall/router. It is not currently routing traffic. Its intended scope and interface assignments were for learning purposes, not consistent use.

## Systems administration and operations

Windows Server 2022 with Active Directory, organizational units, Group Policy, and account controls. It also includes monitoring, centralized logs, internal documentation, and version control.

## Skills illustrated

- Virtualization: VM and container configuration in Proxmox.
- Networking: virtual bridges, guest connectivity, VLAN concepts, routing, and firewall-management access.
- Systems administration: Windows Server, Active Directory, Group Policy, and Linux services.
- Troubleshooting: separating physical, hypervisor, guest, and access-control issues.
- Documentation: recording configuration, investigation steps, and verification boundaries.

## Related work

- [Infrastructure Automation Platform](https://github.com/Bailey7220/infrastructure-automation-platform)

## Privacy

Personal lab only. Do not publish credentials, secrets, public addresses, identifying hostnames, or unredacted configuration exports.
