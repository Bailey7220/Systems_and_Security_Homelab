# VM Networking and OPNsense: Troubleshooting Approach

## Scope

An investigation guide for VM startup, guest connectivity, and OPNsense web-interface access in a Proxmox lab. The server is currently powered off. This document does not claim a verified root cause or successful incident resolution.

## Describe the symptom first

Distinguish between:

- A VM that will not start.
- A running VM whose console works but whose network does not.
- A reachable guest whose web-management interface does not respond.

Record the exact error and the last known change before modifying settings.

## Investigation sequence

| Layer | What to inspect | What to record |
|---|---|---|
| Physical | Server NIC link, cabling, and relevant switch port | Actual connected interfaces and link state |
| Proxmox | VM adapter attachment and whether its bridge exists | Configured bridge name and bridge membership |
| Guest | Console-reported interfaces, addresses, masks, and routes | Actual guest configuration rather than assumed mappings |
| OPNsense | WAN/LAN assignment and the client's path to management | Which adapter reaches which network |
| Access controls | Relevant VLAN membership, routing, and firewall rules | Specific allowed or blocked path and supporting evidence |

Do not assume that a bridge name such as `vmbr0` proves it is WAN or LAN. Confirm the adapter-to-bridge-to-network mapping.

## Safe working boundaries

- Record the existing configuration and preserve console access before changing networking.
- Do not change the Proxmox management path while investigating unrelated guest connectivity unless required and a recovery path is available.
- Change one relevant setting at a time and record the result.
- Do not disable firewall protections broadly or expose the management interface to the internet as a shortcut.

## Verification after a change

Check the specific original symptom: VM startup, intended guest connectivity, or management access from the intended client network. A successful ping alone does not verify web-interface access or correct network isolation.

If isolation is part of the intended design, verify both permitted access and access that should remain blocked. Record the test endpoints and outcomes without publishing sensitive addressing.

## Convert a real investigation into a case study

After testing, document:

1. Observed problem and exact error.
2. Intended behavior.
3. Checks performed and what each showed.
4. Evidence identifying the cause.
5. The change made.
6. Verification results and remaining limitations.

Until those observations are available, this remains a troubleshooting approach rather than a completed incident report.
