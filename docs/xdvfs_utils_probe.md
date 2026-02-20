# XdvFsUtilsProbe

- Source: `xdv-xdvfs-utils/src/xdvfs_utils_probe.ds`
- Summary: xdv-xdvfs-utils: probe workflows

## Purpose
xdv-xdvfs-utils: probe workflows

## Public Procedures
| Procedure | Parameters | Description |
|---|---|---|
| `blkid` | `device: Str` | Performs blkid operation. |
| `lsblk` | `(none)` | Performs lsblk operation. |
| `probe_all` | `(none)` | Performs probe all operation. |

## Status And Error Codes
- `STATUS_OK` (`UInt32`): `0`
- `STATUS_PROBE_FAILED` (`UInt32`): `1`
- `STATUS_PARTITION_UNKNOWN` (`UInt32`): `2`
- `STATUS_SUPERBLOCK_INVALID` (`UInt32`): `3`

## Operational Constants
- `FS_KIND_UNKNOWN` (`UInt32`): `0`
- `FS_KIND_XDVFS` (`UInt32`): `1`
- `PARTITION_STYLE_NONE` (`UInt32`): `0`
- `SUPERBLOCK_OK` (`UInt32`): `1`
- `DEFAULT_DEVICE_HANDLE` (`UInt64`): `1`
- `DEFAULT_TOTAL_BLOCKS` (`UInt64`): `16384`

## Runtime Dependencies
- Detected utility/runtime call usage:
- `create_superblock(...)`
- `detect_partition_table(...)`
- `enumerate_block_devices(...)`
- `enumerate_partitions(...)`
- `probe_standard_storage(...)`
- `validate_superblock(...)`

## Integration Notes
- This module is intended for CLI and runtime utility workflows in xdvfs operations.
- It can be consumed by shell-facing command layers or higher-level orchestration utilities.

## Example (DPL)
```dust
let status = blkid("/dev/xdv0");
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
