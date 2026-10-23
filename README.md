# Systems & Security Homelab

A personal learning lab for virtualization, VM networking, systems administration, monitoring, and security on dedicated server hardware.

> Status: the lab is powered off. This repository documents learning and previously described components, not an active production service. The component inventory is not a claim that every service has been independently verified or is currently running.

## Published work and evidence boundaries

- [VM networking and OPNsense troubleshooting approach](docs/vm-networking-opnsense.md): a structured investigation guide, not a completed incident case study.
- Environment overview below: previously documented hardware and software context, not a deployment or health-test record.
- Related automation code lives in a separate repository linked below.

No measured uptime, operational savings, verified network isolation, or successful backup restore is claimed here. A future case study should include actual observations, changes, and test outcomes rather than a hypothetical success narrative.

## Learning focus

Understand how Proxmox virtual machines connect through virtual bridges, how OPNsense interfaces relate to those connections, and how to investigate loss of VM or firewall-management access.

The troubleshooting approach separates four layers:

1. Physical connections: server NICs, switch ports, and upstream connectivity.
2. Proxmox networking: bridges, attached interfaces, and VM network adapters.
3. Guest configuration: interfaces, addresses, masks, and routes.
4. Access controls: relevant VLAN configuration, routing, and firewall rules.

OPNsense was previously described as a virtualized firewall/router. It is not currently routing traffic. Historical interface assignments and learning configurations should not be treated as a verified present-day topology.

## Historical environment overview

| Layer | Previously documented components |
|---|---|
| Hardware | Dell PowerEdge R630, Dell iDRAC, Cisco managed switch, ASUS router |
| Virtualization | Proxmox VE, KVM virtual machines, LXC containers |
| Networking | OPNsense VM, VLANs, switch ACLs, isolated lab subnet |
| Identity | Windows Server 2022, Active Directory, organizational units, Group Policy |
| Infrastructure services | Pi-hole, NGINX Proxy Manager, TrueNAS |
| Backup and monitoring | Proxmox Backup Server, Zabbix, Grafana, Kibana |
| Applications | GitLab, BookStack, Home Assistant, Jellyfin |

This inventory preserves historical project context. It does not establish current patch levels, deployment completeness, successful restores, or the security of a running environment.

## Skills practiced

- Virtualization and VM/container configuration.
- Virtual bridges, guest connectivity, VLAN concepts, and firewall-management paths.
- Windows/Linux administration, Active Directory, and Group Policy concepts.
- Layered troubleshooting and technical documentation.

Judge implemented work by supporting evidence rather than the number of technologies in the inventory.

## Related work

[Infrastructure Automation Platform](https://github.com/Bailey7220/infrastructure-automation-platform) contains Terraform, Ansible, and static-check configuration. This homelab repository focuses on environment context and troubleshooting documentation; the automation repository has its own status and verification limits.

## Privacy and safe documentation

Personal lab only. Do not publish credentials, private keys, public addresses, identifying hostnames, or unredacted configuration exports. Preserve console access and a recovery path before changing management networking. Do not broadly disable protections merely to make a connectivity test pass.

## Licensing

Original documentation and original project code are available under the [MIT License](LICENSE), subject to [licensing scope](LICENSING.md). Third-party software and assets retain their applicable terms.
