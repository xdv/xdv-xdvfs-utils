# XdvFsUtilsCli

- Source: `xdv-xdvfs-utils/src/xdvfs_utils_cli.ds`
- Summary: xdv-xdvfs-utils: command orchestration entrypoints

## Purpose
xdv-xdvfs-utils: command orchestration entrypoints

## Public Procedures
| Procedure | Parameters | Description |
|---|---|---|
| `run_probe` | `device: Str` | Performs run probe operation. |
| `run_partition` | `device: Str` | Performs run partition operation. |
| `run_mkfs` | `device: Str` | Performs run mkfs operation. |
| `run_fsck` | `device: Str` | Performs run fsck operation. |
| `run_dir` | `path: Str` | Performs run dir operation. |
| `run_file` | `path: Str` | Performs run file operation. |
| `run_mount` | `device: Str` | Performs run mount operation. |
| `run_space` | `target: Str` | Performs run space operation. |
| `run_perm` | `path: Str` | Performs run perm operation. |
| `run` | `tool: UInt32, device: Str` | Performs run operation. |

## Status And Error Codes
- `STATUS_OK` (`UInt32`): `0`
- `STATUS_INVALID_TOOL` (`UInt32`): `1`

## Operational Constants
- `TOOL_PROBE` (`UInt32`): `1`
- `TOOL_PARTITION` (`UInt32`): `2`
- `TOOL_MKFS` (`UInt32`): `3`
- `TOOL_FSCK` (`UInt32`): `4`
- `TOOL_DIR` (`UInt32`): `5`
- `TOOL_FILE` (`UInt32`): `6`
- `TOOL_MOUNT` (`UInt32`): `7`
- `TOOL_SPACE` (`UInt32`): `8`
- `TOOL_PERM` (`UInt32`): `9`

## Runtime Dependencies
- Detected utility/runtime call usage:
- `blkid(...)`
- `dir_ls(...)`
- `fdisk_print(...)`
- `file_touch(...)`
- `fsck_xdvfs(...)`
- `lsblk(...)`
- `mkfs_xdvfs(...)`
- `mount_xdvfs(...)`
- `perm_chmod(...)`
- `space_df(...)`

## Integration Notes
- This module is intended for CLI and runtime utility workflows in xdvfs operations.
- It can be consumed by shell-facing command layers or higher-level orchestration utilities.

## Example (DPL)
```dust
let status = run_probe("/dev/xdv0");
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
