# Mission 03 — The Vanishing Disk

## Briefing
A workload reports “disk full,” yet the host appears to have free capacity. Another service claims its expected path does not exist after reboot.

## Objective
Understand RHEL block devices, partitions, LVM, XFS, mounts, inodes, paths, and persistent mount configuration.

## Build
Attach a disposable VM disk. Inspect it before changing anything, then build a small RHEL-style storage path. Prefer an LVM-backed XFS filesystem so the exercise includes physical volume → volume group → logical volume → filesystem → mount point. Mount it, write data, inspect capacity and inode usage, and make the mount persistent with a stable identifier in `/etc/fstab`.

Useful tools include `lsblk`, `blkid`, `pvs`, `vgs`, `lvs`, `xfs_info`, `findmnt`, `df`, and `du`.

Validate the `fstab` entry with `mount -a` before rebooting.

## Deliberate failure
Choose one safe, reversible case: fill the small filesystem, create a mount/path mismatch, use a bad lab-only `fstab` entry, leave a logical volume unavailable, or intentionally omit the lab mount after reboot.

Do not deliberately damage the root filesystem or the VM's boot storage.

## Investigation
Use `lsblk`, `pvs`, `vgs`, `lvs`, `findmnt`, `df -hT`, `df -i`, `du`, `mount`, `blkid`, `systemctl --failed`, and journal output. Determine whether the problem is device/LVM state, filesystem capacity, mount configuration, missing mount, path ownership, or the application path itself.

## Evidence to save
- storage path diagram: disk/partition → PV → VG → LV → XFS → mount point → application path
- working persistent mount configuration
- before/failure/after capacity and mount evidence
- root-cause proof and validation after repair

## Victory condition
You can trace the complete RHEL storage path and explain why “disk full” or “the data disappeared” is an application symptom rather than a diagnosis.
