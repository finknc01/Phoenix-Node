# Final Mission — Phoenix Rising

## Briefing
PHX-07 has passed individual repairs. Now the operations lead wants proof that the node is recoverable as a system.

## Scenario
Start from a fresh disposable Ubuntu environment or a deliberately reset lab VM. Assume the original operator is unavailable. Your repository is the only runbook.

## Objective
Recreate the documented host state, validate it, inject two unrelated failures, diagnose them from evidence, recover them, and produce a handoff report.

## Required demonstration
1. Baseline the fresh node.
2. Apply your documented configuration/automation.
3. Validate users, services, storage paths, networking, and GPU/runtime layers that are actually available in the environment.
4. Introduce two safe faults from different layers without looking at your old incident notes.
5. Diagnose them systematically.
6. Re-run validation and automation after recovery.

## Final evidence
- architecture diagram
- provisioning/automation source
- validation output
- two incident reports
- recovery timeline
- “what I would change in production” section

## Victory condition
A second engineer could use the repository to understand what PHX-07 is, rebuild the lab version, validate it, and follow your troubleshooting logic.

Phoenix-Node is complete when the node is no longer a mysterious machine. It is a system you can explain and recover.
