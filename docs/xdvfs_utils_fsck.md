# XdvFsUtilsFsck

- Source: `xdv-xdvfs-utils/src/xdvfs_utils_fsck.ds`
- Summary: xdv-xdvfs-utils: fsck workflows

## Purpose
xdv-xdvfs-utils: fsck workflows

## Public Procedures
| Procedure | Parameters | Description |
|---|---|---|
| `fsck_xdvfs` | `device: Str, repair_mode: UInt32` | Performs fsck xdvfs operation. |
| `fsck_auto_repair` | `device: Str` | Performs fsck auto repair operation. |
| `fsck_read_only` | `device: Str` | Performs fsck read only operation. |

## Status And Error Codes
- `STATUS_OK` (`UInt32`): `0`
- `STATUS_FSCK_FAILED` (`UInt32`): `1`
- `STATUS_REPAIR_REQUIRED` (`UInt32`): `2`

## Operational Constants
- `REPAIR_MODE_NONE` (`UInt32`): `0`
- `REPAIR_MODE_SAFE` (`UInt32`): `1`
- `REPAIR_MODE_AGGRESSIVE` (`UInt32`): `2`
- `DEFAULT_DEVICE_HANDLE` (`UInt64`): `1`
- `DEFAULT_TOTAL_BLOCKS` (`UInt64`): `16384`
- `SUPERBLOCK_OK` (`UInt32`): `1`

## Runtime Dependencies
- Detected utility/runtime call usage:
- `create_superblock(...)`
- `detect_partition_table(...)`
- `format_filesystem(...)`
- `probe_standard_storage(...)`
- `validate_superblock(...)`

## Integration Notes
- This module is intended for CLI and runtime utility workflows in xdvfs operations.
- It can be consumed by shell-facing command layers or higher-level orchestration utilities.

## Example (DPL)
```dust
let status = fsck_xdvfs("/dev/xdv0", 1);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
