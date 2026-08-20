# Mission 00 — Triage PHX-07

## Briefing
PHX-07 has been removed from service after a string of unexplained failures. Before changing anything, you must build a trustworthy picture of the machine as it exists now.

## Objective
Create a baseline of the host and explain what must be true before it can be considered safe to troubleshoot further.

## Constraints
- Do not reinstall the OS.
- Do not change packages or services until you have captured the baseline.
- Every conclusion must point to evidence.

## Tasks
1. Identify OS, kernel, CPU, memory, disks, network interfaces, default route, running services, failed services, logged-in users, and recent boot history.
2. Record the boot chain you expect from firmware to userspace.
3. Capture the output of `uname -a`, `cat /etc/os-release`, `lscpu`, `free -h`, `lsblk`, `ip addr`, `ip route`, `systemctl --failed`, and a short `journalctl -b` review.
4. Draw a one-page host map showing hardware, kernel, services, storage, networking, and where the GPU runtime will eventually sit.
5. Write down three plausible failure domains based on the evidence you actually collected.

## Deliberate problem
Choose one harmless, reversible issue such as a stopped non-critical service or a disabled lab-only unit. Record the symptom before fixing it.

## Evidence to save
- `evidence/mission-00-baseline.md`
- architecture sketch
- command outputs or concise excerpts
- before/after state for the deliberate problem

## Victory condition
You can explain PHX-07 from power-on to a running service and identify where you would look first for a boot, storage, service, or network failure without guessing.

## Debrief
- Which observations came from hardware, kernel, and userspace respectively?
- Which command gave you the most useful signal?
- What did you initially assume that the evidence corrected?
