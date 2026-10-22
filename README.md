# Systems & Security Homelab

A personal lab developed to practice virtualization, VM networking, systems administration, monitoring, and security on dedicated server hardware.

> Current status: the server is unplugged and none of the lab services are running. The lab can be powered on for further practice, but its current functionality has not been revalidated. This repository describes the previously documented setup, not a live production environment.

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

This is an inventory, not a verified current topology. Exact cabling, bridge-to-NIC assignments, VLAN paths, and OPNsense interface mappings must be checked when the lab is powered on.

## Virtualization and networking

Proxmox hosts full virtual machines and lightweight containers. The previously documented network design used managed-switch VLANs and access controls to separate traffic, with an isolated subnet for lab workloads.

The networking work focuses on distinguishing four layers:

1. Physical connections: server NICs, switch ports, and upstream connectivity.
2. Proxmox networking: bridges, attached interfaces, and VM network adapters.
3. Guest configuration: assigned interfaces, addresses, masks, and routes.
4. Access controls: relevant VLAN configuration and firewall rules.

OPNsense was documented as a virtualized firewall/router. It is not currently routing traffic. Its intended scope and interface assignments need confirmation before reuse.

## Systems administration and operations

The earlier setup documented Windows Server 2022 with Active Directory, organizational units, Group Policy, and account controls. It also included backup scheduling, monitoring, centralized logs, internal documentation, and version control.

These are historical configuration descriptions, not evidence that patching, monitoring, or scheduled backups are currently operating. No successful restore test is claimed here.

## Skills illustrated

- Virtualization: VM and container configuration in Proxmox.
- Networking: virtual bridges, guest connectivity, VLAN concepts, routing, and firewall-management access.
- Systems administration: Windows Server, Active Directory, Group Policy, and Linux services.
- Troubleshooting: separating physical, hypervisor, guest, and access-control issues.
- Documentation: recording configuration, investigation steps, and verification boundaries.

## Evidence and limitations

This repository currently provides written documentation. It does not yet include sanitized screenshots, configuration exports, or a confirmed incident-resolution case study.

The linked troubleshooting guide is an investigation framework, not proof that every check was performed or that a particular fix succeeded. Additional services are listed for context; their inclusion does not imply production-scale expertise.

When the server is powered on again, useful additions would be two sanitized screenshots, a verified architecture diagram, and one real troubleshooting example with its observed outcome. None requires expanding the lab's technical scope.

## Related work

- [Infrastructure Automation Platform](https://github.com/Bailey7220/infrastructure-automation-platform)

Related repositories have their own scope and are not evidence that this lab is currently running.

## Privacy

Personal lab only. Do not publish credentials, secrets, public addresses, identifying hostnames, or unredacted configuration exports.
