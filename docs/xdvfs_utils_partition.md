# XdvFsUtilsPartition

- Source: `xdv-xdvfs-utils/src/xdvfs_utils_partition.ds`
- Summary: xdv-xdvfs-utils: partitioning workflows

## Purpose
xdv-xdvfs-utils: partitioning workflows

## Public Procedures
| Procedure | Parameters | Description |
|---|---|---|
| `is_supported_partition_type` | `partition_type: UInt32` | Performs is supported partition type operation. |
| `fdisk_print` | `device: Str` | Performs fdisk print operation. |
| `fdisk_create_mbr` | `device: Str` | Performs fdisk create mbr operation. |
| `fdisk_create_gpt` | `device: Str` | Performs fdisk create gpt operation. |
| `fdisk_add_partition` | `device: Str, start_lba: UInt64, sector_count: UInt64, partition_type: UInt32` | Performs fdisk add partition operation. |
| `fdisk_set_bootable` | `device: Str, partition_index: UInt32` | Performs fdisk set bootable operation. |

## Status And Error Codes
- `STATUS_OK` (`UInt32`): `0`
- `STATUS_INVALID_DEVICE` (`UInt32`): `1`
- `STATUS_PARTITION_OP_FAILED` (`UInt32`): `2`
- `STATUS_INVALID_PARTITION_TYPE` (`UInt32`): `3`

## Operational Constants
- `LABEL_MBR` (`UInt32`): `1`
- `LABEL_GPT` (`UInt32`): `2`
- `PARTITION_STYLE_NONE` (`UInt32`): `0`
- `PARTITION_TYPE_XDVFS` (`UInt32`): `227`
- `PARTITION_TYPE_LINUX` (`UInt32`): `131`
- `PARTITION_TYPE_FAT32_LBA` (`UInt32`): `12`
- `PARTITION_OK` (`UInt32`): `0`
- `DEFAULT_DEVICE_HANDLE` (`UInt64`): `1`
- `DEFAULT_PARTITION_SECTORS` (`UInt64`): `65536`

## Runtime Dependencies
- Detected utility/runtime call usage:
- `create_gpt_partition_table(...)`
- `create_mbr_partition_table(...)`
- `create_partition(...)`
- `detect_partition_table(...)`
- `enumerate_partitions(...)`
- `layout_mbr_64m(...)`
- `probe_standard_storage(...)`
- `set_partition_bootable(...)`

## Integration Notes
- This module is intended for CLI and runtime utility workflows in xdvfs operations.
- It can be consumed by shell-facing command layers or higher-level orchestration utilities.

## Example (DPL)
```dust
let status = is_supported_partition_type(1);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
