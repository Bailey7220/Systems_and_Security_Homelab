# Enterprise Homelab

A self-built, enterprise-style lab environment used to develop hands-on skills in virtualization, networking, systems administration, monitoring, and security. The lab runs production-pattern services on dedicated server hardware behind a managed switch and a segmented network.

This repository documents the architecture, the services running in it, and the operational practices used to maintain it.

---

## Why this exists

Reading about VLANs, Active Directory, and monitoring stacks is not the same as running them. This lab exists to build and operate the same categories of infrastructure that businesses depend on — hypervisors, directory services, DNS, reverse proxies, backups, log aggregation, and metrics — and to troubleshoot them when they break.

---

## Physical infrastructure

| Component | Role |
|---|---|
| Dell PowerEdge R630 | Primary virtualization host |
| Dell iDRAC | Out-of-band management and remote console |
| Cisco managed switch | VLAN segmentation, port configuration, ACLs |
| ASUS router | Upstream gateway |
| TrueNAS | Network-attached storage |

---

## Virtualization platform

**Proxmox VE** is the hypervisor, running both full virtual machines (KVM) and lightweight system containers (LXC). Container-based workloads are used where a full VM is unnecessary, which reduces resource overhead on the host.

**Proxmox Backup Server** provides scheduled, deduplicated backups of guest workloads.

---

## Services running in the lab

### Infrastructure and networking

| Service | Type | Purpose |
|---|---|---|
| OPNsense | VM | Firewall and routing, network segmentation enforcement |
| Pi-hole | VM | Network-wide DNS filtering and DNS resolution |
| NGINX Proxy Manager | CT | Reverse proxy and TLS certificate management for internal services |
| TrueNAS | VM | Centralized storage |

### Directory and identity

Windows Server 2022 running **Active Directory Domain Services**, with organizational units, group policy objects, account controls, and patch management applied to domain-joined systems.

### Monitoring and observability

| Service | Purpose |
|---|---|
| Zabbix | Infrastructure monitoring and alerting |
| Grafana | Metrics dashboards and visualization |
| Kibana | Log search and analysis |

### Applications

| Service | Type | Purpose |
|---|---|---|
| GitLab | VM | Self-hosted Git repositories and CI |
| BookStack | CT | Internal documentation and runbooks |
| Home Assistant | VM | Home automation platform |
| Jellyfin | VM | Media services |

---

## Network design

The lab uses VLAN segmentation on the Cisco managed switch to separate traffic by function, with an isolated subnet used for testing and lab workloads that should not reach the primary network. Access control lists restrict traffic between segments rather than relying on a single flat network.

Internal services are reached through a reverse proxy rather than exposing individual ports, and DNS resolution is handled internally.

---

## Operational practices

- **Backups** — scheduled guest backups through Proxmox Backup Server
- **Patch management** — controlled update process for domain-joined Windows systems
- **Account controls** — group policy enforcement, least-privilege service accounts
- **Documentation** — runbooks and configuration notes maintained in BookStack
- **Version control** — configuration and scripts tracked in self-hosted GitLab
- **Monitoring** — host and service health monitored with alerting, metrics dashboards, and centralized logs

---

## Skills demonstrated

**Virtualization** — Proxmox VE, KVM virtual machines, LXC containers, resource allocation, Proxmox Backup Server

**Networking** — VLANs, subnetting, access control lists, managed switch configuration, firewall rules, DNS, reverse proxy, TLS

**Systems administration** — Windows Server 2022, Active Directory, group policy, Ubuntu Linux, out-of-band management via iDRAC

**Monitoring and logging** — Zabbix, Grafana, Kibana

**Security** — network segmentation, DNS filtering, account controls, patch management

**Documentation** — architecture documentation, runbooks, change notes

---

## Related repositories

- [Infrastructure Automation Platform](https://github.com/Bailey7220/infrastructure-automation-platform) — Terraform and Ansible provisioning for this Proxmox environment
- [SOC ELK Wazuh](https://github.com/Bailey7220/soc-elk-wazuh) — automated deployment of an ELK and Wazuh security monitoring stack

---

*Personal lab environment. No production or third-party data. Hostnames, addressing, and credentials are not published.*
