# xdv-xdvfs-utils

Version: 0.2.0  
Status: Active  
Language: Dust Programming Language (DPL)

## Purpose

`xdv-xdvfs-utils` is an independent utility workspace for the XDV filesystem stack.

It provides DPL-native workflows equivalent to common industry storage tools:

- Partitioning (fdisk/parted style)
- Formatting (mkfs style)
- Integrity checking (fsck style)
- Device/probe reporting (blkid/lsblk style)
- Directory management (mkdir/rmdir/ls/tree style)
- File management (text + binary read/write/copy/move/delete style)
- Mount lifecycle operations (mount/umount/remount/sync style)
- Capacity and I/O statistics (df/du/stat/iostat style)
- Permission and ownership metadata operations (chmod/chown/chgrp/umask style)

## Layout

`src/xdvfs_utils_partition.ds`  
Partition table and partition-entry management workflows.

`src/xdvfs_utils_mkfs.ds`  
Filesystem creation workflows for xdvfs and compatibility targets.

`src/xdvfs_utils_fsck.ds`  
Filesystem integrity and repair workflows.

`src/xdvfs_utils_probe.ds`  
Storage probe and reporting workflows.

`src/xdvfs_utils_dir.ds`  
Directory lifecycle and listing workflows.

`src/xdvfs_utils_file.ds`  
Plain-text and binary file operation workflows.

`src/xdvfs_utils_mount.ds`  
Mount/unmount/remount/sync orchestration workflows.

`src/xdvfs_utils_space.ds`  
Filesystem capacity and I/O statistics workflows.

`src/xdvfs_utils_perm.ds`  
Permission and ownership metadata workflows.

`src/xdvfs_utils_cli.ds`  
Shared utility command orchestration entrypoints.

## Build

```bash
dust check xdv-xdvfs-utils/src
```
