# Mission 02 — Locked Out of Your Own Machine

## Briefing
A rushed hardening change leaves the maintenance account unable to perform an operation it completed yesterday. The host is healthy; identity and authorization are not.

## Objective
Learn Linux users, groups, ownership, permissions, sudo, SSH key permissions, and service accounts as one access-control system.

## Build
Create lab-only users and groups. Give one service account access to a protected directory and one operator limited sudo rights.

## Deliberate failure
Break one safe permission boundary: wrong ownership on a lab directory, incorrect SSH key permissions in a VM, or removal of a lab user from a required group.

## Investigation
Use `id`, `getent`, `namei -l`, `ls -l`, `stat`, `sudo -l`, auth logs, and SSH verbose output where appropriate. Trace the exact authorization check that fails.

## Evidence to save
- access matrix: user/group/resource/required permission
- failed command and exact error
- evidence identifying the denied check
- corrected state and validation

## Victory condition
You can explain the difference between authentication, authorization, ownership, mode bits, groups, and sudo policy using the incident you created.

## Debrief
- Why was the failure not a networking problem even if it appeared during SSH?
- What is the narrowest safe fix?
