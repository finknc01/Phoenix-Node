# Mission 02 — Locked Out of Your Own Machine

## Briefing
A rushed hardening change leaves the maintenance account unable to perform an operation it completed yesterday. The host is healthy; identity, authorization, or mandatory access control is not.

## Objective
Learn RHEL users, groups, ownership, permissions, sudo, SSH key permissions, service accounts, and SELinux as one access-control system.

## Build
Create lab-only users and groups. Give one service account access to a protected directory and one operator limited sudo rights. Confirm SELinux is enforcing with `getenforce`/`sestatus` and inspect labels with `ls -Z` and `ps -eZ`.

## Deliberate failure
Create two safe, reversible failures:

1. one traditional UNIX permission failure, such as wrong ownership on a lab directory, incorrect SSH key permissions, or removal of a lab user from a required group;
2. one lab-only SELinux labeling/context problem that denies an otherwise valid access path.

Do not solve the SELinux case by setting SELinux to permissive or disabled.

## Investigation
Use `id`, `getent`, `namei -l`, `ls -l`, `stat`, `sudo -l`, authentication logs, and SSH verbose output where appropriate. For SELinux, use `getenforce`, `ls -Z`, `ausearch -m AVC`, and relevant journal/audit evidence. Trace the exact authorization check that fails.

Restore the SELinux case with the correct context/policy mechanism, such as `restorecon` or an appropriate persistent file-context rule, rather than weakening enforcement globally.

## Evidence to save
- access matrix: user/group/resource/required permission
- failed command and exact error
- traditional permission evidence identifying the denied check
- SELinux AVC/context evidence and the corrected label/policy state
- corrected state and validation for both allowed and denied cases

## Victory condition
You can explain the difference between authentication, discretionary authorization, ownership/mode bits, groups, sudo policy, and SELinux mandatory access control using failures you created and proved.

## Debrief
- Why was the failure not a networking problem even if it appeared during SSH?
- What is the narrowest safe fix?
- How can UNIX permissions appear correct while SELinux still denies access?
- Why is disabling SELinux a poor troubleshooting fix?
