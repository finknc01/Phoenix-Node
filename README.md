# Phoenix-Node

> **Project Phoenix — resurrect a distrusted AI compute node, understand every layer that makes it live, then prove you can rebuild it from evidence instead of memory.**

## Project status

| Field | Current state |
|---|---|
| **Status** | **Active — foundation project** |
| **Current stage** | Ready to begin Mission 00; no mission completion is claimed yet |
| **Primary environment** | Ubuntu Server VM for core Linux work |
| **GPU environment** | A real Linux host with direct NVIDIA GPU access is required for Linux driver-installation/troubleshooting evidence; native/dual-boot Linux, another physical Linux GPU host, or a supported temporary cloud GPU are valid options |
| **Modeled work** | Enterprise-only hardware, topology, BMC, NVLink/NVSwitch, or other unavailable features must be labeled modeled/reference |
| **Last plan sync** | 2026-08-19 |

## Purpose

Phoenix-Node is the single-host foundation for the portfolio. You inherit fictional node **PHX-07**, which was removed from service after poorly documented boot, storage, SSH, service, and GPU-software problems.

The objective is not merely to make the machine work. It is to make its state explainable, its failures diagnosable, and its rebuild repeatable.

> **If this node failed tonight, could I identify the broken layer, prove the cause, restore service, and rebuild the host without undocumented memory?**

## Skills developed

- Linux boot and userspace boundaries
- users, groups, permissions, SSH, storage, mounts, services, and networking
- `systemd`, journals, process and dependency troubleshooting
- NVIDIA driver/CUDA/runtime boundaries
- GPU validation and basic health checks where supported
- Bash, Python/Ansible, idempotency, and repeatable provisioning
- failure injection, evidence collection, incident reporting, and recovery

## Mission campaign

The files in [`missions/`](missions/) are authoritative. The campaign is intentionally compact so it fits the 52-week learning plan.

| Mission | Incident / objective | Primary outcome |
|---|---|---|
| [00 — Triage PHX-07](missions/00-triage.md) | Establish a trustworthy baseline before changing anything | inventory + host map + first hypotheses |
| [01 — The Boot That Never Finished](missions/01-boot-chain.md) | Follow firmware/bootloader/kernel/initramfs/systemd boundaries and diagnose a safe boot-time failure | boot-chain evidence + first-bad-unit reasoning |
| [02 — Access Control](missions/02-access-control.md) | Build and troubleshoot users, groups, permissions, sudo, and SSH access | repeatable access model |
| [03 — The Vanishing Disk](missions/03-storage.md) | Understand block devices, filesystems, mounts, persistence, and storage failure symptoms | persistent storage configuration + recovery evidence |
| [04 — Alive but Unreachable](missions/04-host-network.md) | Trace host networking, routes, DNS, sockets, and reachability | host-network diagnosis |
| [05 — The Driver Rift](missions/05-gpu-stack.md) | Bring a real Linux GPU host through driver → CUDA/runtime → validation | documented GPU software compatibility state |
| [06 — Ashes to Automation](missions/06-automation.md) | Convert repeatable host configuration into controlled automation | reproducible configuration artifacts |
| [Final — Phoenix Rising](missions/final-phoenix-rising.md) | Recover and rebuild PHX-07 from documented evidence and source-controlled truth | end-to-end recovery narrative |

## GPU environment rule

A normal Ubuntu VM is sufficient for Missions 00–04 and much of Mission 06, but it does not automatically provide meaningful Linux GPU-driver administration. Before Mission 05, choose an environment where Linux has direct, supported NVIDIA GPU access.

WSL can be useful for supplementary CUDA/container exercises, but it should not be presented as evidence that you installed or troubleshot the Linux NVIDIA kernel driver when the driver is actually owned by the Windows host.

## Evidence standard

For every mission, save enough evidence that another engineer could follow the reasoning:

1. expected healthy state or path
2. symptom
3. observations
4. hypothesis
5. test
6. root cause
7. fix
8. validation
9. prevention/monitoring idea

Use [`evidence/`](evidence/) for real artifacts, [`incidents/`](incidents/) for incident writeups, [`configs/`](configs/) for sanitized configuration, [`diagrams/`](diagrams/) for architecture, and [`automation/`](automation/) for repeatable build work.

Every artifact must distinguish **measured**, **derived**, and **modeled/reference** information.

## Completion condition

Phoenix-Node is complete when PHX-07 is no longer mysterious: the important host layers are documented, one or more failures have been diagnosed from evidence, the GPU software boundary is understood on a real supported environment, and meaningful parts of the host can be recreated predictably from repository-controlled artifacts.
