# XdvFsUtilsSpace

- Source: `xdv-xdvfs-utils/src/xdvfs_utils_space.ds`
- Summary: xdv-xdvfs-utils: capacity/statistics workflows

## Purpose
xdv-xdvfs-utils: capacity/statistics workflows

## Public Procedures
| Procedure | Parameters | Description |
|---|---|---|
| `space_df` | `device: Str, mount_point: Str` | Performs space df operation. |
| `space_du` | `path: Str` | Performs space du operation. |
| `space_stat` | `path: Str` | Performs space stat operation. |
| `space_iostat` | `device: Str` | Performs space iostat operation. |

## Status And Error Codes
- `STATUS_OK` (`UInt32`): `0`
- `STATUS_SPACE_FAILED` (`UInt32`): `1`
- `STATUS_PATH_NOT_FOUND` (`UInt32`): `2`

## Operational Constants
- `ROOT_INODE` (`UInt64`): `2`
- `IO_SAMPLE_SECTORS` (`UInt32`): `128`
- `DEFAULT_DEVICE_HANDLE` (`UInt64`): `1`
- `INVALID_RESULT` (`UInt32`): `0`

## Runtime Dependencies
- Detected utility/runtime call usage:
- `flush_storage_cache(...)`
- `get_fs_stats(...)`
- `get_inode(...)`
- `get_logical_sector_size(...)`
- `lookup(...)`
- `mount(...)`
- `probe_standard_storage(...)`
- `read_sectors(...)`
- `readdir(...)`
- `write_sectors(...)`

## Integration Notes
- This module is intended for CLI and runtime utility workflows in xdvfs operations.
- It can be consumed by shell-facing command layers or higher-level orchestration utilities.

## Example (DPL)
```dust
let status = space_df("/dev/xdv0", "/xdv");
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
