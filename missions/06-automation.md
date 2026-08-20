# Mission 06 — Ashes to Automation

## Briefing
The team no longer trusts hand-built nodes. PHX-07 must become reproducible.

## Objective
Turn your successful manual configuration into repeatable, reviewable automation.

## Build
Automate a useful subset of the host: packages, users/groups, directories, service configuration, validation checks, and optionally NVIDIA/container prerequisites where safe.

Start with Bash for transparent steps, then move repeatable state into Ansible. Keep secrets out of the repository.

## Deliberate failure
Introduce configuration drift: change a managed file, stop a managed service, alter a permission, or remove a lab package.

## Investigation and recovery
Run your validation first. Then use automation to converge the node back to the intended state. Record what changed and whether the second automation run is idempotent.

## Evidence to save
- automation source
- before/after drift report
- first and second run outputs
- validation script output

## Victory condition
You can rebuild or repair the selected host state without relying on memory or undocumented manual steps.
