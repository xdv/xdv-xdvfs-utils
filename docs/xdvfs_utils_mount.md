# XdvFsUtilsMount

- Source: `xdv-xdvfs-utils/src/xdvfs_utils_mount.ds`
- Summary: xdv-xdvfs-utils: mount workflows

## Purpose
xdv-xdvfs-utils: mount workflows

## Public Procedures
| Procedure | Parameters | Description |
|---|---|---|
| `mount_xdvfs` | `device: Str, mount_point: Str` | Performs mount xdvfs operation. |
| `mount_read_only` | `device: Str, mount_point: Str` | Performs mount read only operation. |
| `mount_remount` | `mount_point: Str, flags: UInt32` | Performs mount remount operation. |
| `mount_sync` | `mount_point: Str` | Performs mount sync operation. |
| `mount_umount` | `mount_point: Str` | Performs mount umount operation. |
| `mount_check` | `device: Str` | Performs mount check operation. |

## Status And Error Codes
- `STATUS_OK` (`UInt32`): `0`
- `STATUS_MOUNT_FAILED` (`UInt32`): `1`
- `STATUS_SYNC_FAILED` (`UInt32`): `2`

## Operational Constants
- `MOUNT_FLAGS_DEFAULT` (`UInt32`): `0`
- `MOUNT_FLAGS_RDONLY` (`UInt32`): `1`
- `MOUNT_FLAGS_SYNC` (`UInt32`): `16`
- `DEFAULT_DEVICE_HANDLE` (`UInt64`): `1`

## Runtime Dependencies
- Detected utility/runtime call usage:
- `check_filesystem(...)`
- `mount(...)`
- `remount(...)`
- `sync_filesystem(...)`
- `unmount(...)`

## Integration Notes
- This module is intended for CLI and runtime utility workflows in xdvfs operations.
- It can be consumed by shell-facing command layers or higher-level orchestration utilities.

## Example (DPL)
```dust
let status = mount_xdvfs("/dev/xdv0", "/xdv");
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
