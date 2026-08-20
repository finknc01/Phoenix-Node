# Mission 03 — The Vanishing Disk

## Briefing
A workload reports “disk full,” yet the host appears to have free capacity. Another service claims its expected path does not exist after reboot.

## Objective
Understand block devices, partitions, filesystems, mounts, inodes, paths, and persistent mount configuration.

## Build
Use a loopback file or disposable VM disk to create a small lab filesystem. Mount it, write data, inspect capacity and inode usage, then make the mount persistent in the disposable environment.

## Deliberate failure
Choose one: fill the small filesystem, exhaust a small inode pool, mount the wrong device at the expected path, or intentionally omit the lab mount after reboot.

## Investigation
Use `lsblk`, `findmnt`, `df -h`, `df -i`, `du`, `mount`, `blkid`, and logs. Determine whether the problem is capacity, inode exhaustion, wrong mount, missing mount, or path ownership.

## Evidence to save
- storage path diagram from block device to application path
- before/failure/after capacity metrics
- root-cause proof

## Victory condition
You can explain why “disk full” is an application symptom rather than a diagnosis.
