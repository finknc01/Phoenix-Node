# Phoenix-Node Mission Campaign

PHX-07 is a distrusted AI compute node. Each mission turns one layer of the host into something you can explain, break safely, diagnose, and restore.

## Campaign rules
1. Capture the healthy state before introducing a fault.
2. Predict the symptom before you break anything.
3. Gather evidence before changing configuration.
4. Keep every failure reversible and confined to the lab.
5. Record what you expected, what happened, why, and how you proved the fix.

## Missions
- [00 — Triage PHX-07](00-triage.md)
- [01 — The Boot That Never Finished](01-boot-chain.md)
- [02 — Locked Out of Your Own Machine](02-access-control.md)
- [03 — The Vanishing Disk](03-storage.md)
- [04 — Alive but Unreachable](04-host-network.md)
- [05 — The Driver Rift](05-gpu-stack.md)
- [06 — Ashes to Automation](06-automation.md)
- [Final — Phoenix Rising](final-phoenix-rising.md)

## Evidence standard
For every mission save a short report under `evidence/` with: symptom, expected layer/path, observations, hypothesis, test, root cause, fix, validation, and one production prevention or monitoring idea.
