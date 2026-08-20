# Mission 01 — The Boot That Never Finished

## Briefing
PHX-07 rebooted during maintenance and never returned to service. You have console access, but the normal application stack is missing.

## Objective
Understand the Linux boot path well enough to locate a failure between firmware, bootloader, kernel, initramfs, systemd targets, mounts, and services.

## Build
- Diagram the expected boot chain.
- Record `systemd-analyze`, `systemctl get-default`, critical units, mounts, and dependencies.
- Identify where `/etc/fstab`, kernel parameters, and service ordering can block startup.

## Deliberate failure
In a disposable VM, create a harmless failed lab service or a non-critical mount dependency that causes a unit to fail at boot. Do not sabotage your primary laptop boot path.

## Investigation
Use `journalctl -b`, `systemctl --failed`, `systemctl status`, `systemctl list-dependencies`, and mount information to isolate the first bad unit rather than chasing downstream symptoms.

## Evidence to save
- boot-chain diagram
- failed-unit dependency chain
- relevant journal excerpts
- before/after boot timing

## Victory condition
You can explain why the system reached its current target, which dependency failed first, and why repairing that layer restored the downstream services.

## Debrief
- What was the first failure versus the loudest symptom?
- Which evidence distinguished a service failure from a mount or boot failure?
