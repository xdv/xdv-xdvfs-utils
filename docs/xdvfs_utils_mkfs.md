# XdvFsUtilsMkfs

- Source: `xdv-xdvfs-utils/src/xdvfs_utils_mkfs.ds`
- Summary: xdv-xdvfs-utils: formatting workflows

## Purpose
xdv-xdvfs-utils: formatting workflows

## Public Procedures
| Procedure | Parameters | Description |
|---|---|---|
| `mkfs_xdvfs` | `device: Str` | Performs mkfs xdvfs operation. |
| `mkfs_fat32` | `device: Str` | Performs mkfs fat32 operation. |
| `mkfs_ext2` | `device: Str` | Performs mkfs ext2 operation. |

## Status And Error Codes
- `STATUS_OK` (`UInt32`): `0`
- `STATUS_MKFS_FAILED` (`UInt32`): `1`
- `STATUS_INVALID_DEVICE` (`UInt32`): `2`
- `STATUS_UNSUPPORTED_TARGET` (`UInt32`): `3`

## Operational Constants
- `FS_KIND_XDVFS` (`UInt32`): `1`
- `FS_KIND_FAT32` (`UInt32`): `2`
- `FS_KIND_EXT2` (`UInt32`): `3`
- `DEFAULT_BLOCK_SIZE` (`UInt32`): `4096`
- `DEFAULT_INODE_SIZE` (`UInt32`): `256`
- `DEFAULT_DEVICE_HANDLE` (`UInt64`): `1`
- `DEFAULT_PARTITION_SECTORS` (`UInt64`): `65536`
- `PARTITION_TYPE_XDVFS` (`UInt32`): `227`
- `PARTITION_TYPE_LINUX` (`UInt32`): `131`
- `PARTITION_TYPE_FAT32_LBA` (`UInt32`): `12`

## Runtime Dependencies
- Detected utility/runtime call usage:
- `create_gpt_partition_table(...)`
- `create_mbr_partition_table(...)`
- `create_partition(...)`
- `detect_partition_table(...)`
- `finalize_format(...)`
- `format_xdvfs(...)`
- `layout_mbr_64m(...)`
- `prepare_format_context(...)`
- `probe_standard_storage(...)`

## Integration Notes
- This module is intended for CLI and runtime utility workflows in xdvfs operations.
- It can be consumed by shell-facing command layers or higher-level orchestration utilities.

## Example (DPL)
```dust
let status = mkfs_xdvfs("/dev/xdv0");
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
