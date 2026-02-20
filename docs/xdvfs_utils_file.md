# XdvFsUtilsFile

- Source: `xdv-xdvfs-utils/src/xdvfs_utils_file.ds`
- Summary: xdv-xdvfs-utils: file workflows

## Purpose
xdv-xdvfs-utils: file workflows

## Public Procedures
| Procedure | Parameters | Description |
|---|---|---|
| `file_touch` | `path: Str` | Performs file touch operation. |
| `file_read_text` | `path: Str, char_count: UInt32` | Performs file read text operation. |
| `file_write_text` | `path: Str, char_count: UInt32` | Performs file write text operation. |
| `file_append_text` | `path: Str, char_count: UInt32` | Performs file append text operation. |
| `file_read_binary` | `path: Str, byte_count: UInt32` | Performs file read binary operation. |
| `file_write_binary` | `path: Str, byte_count: UInt32` | Performs file write binary operation. |
| `file_cp` | `src: Str, dst: Str, byte_count: UInt32` | Performs file cp operation. |
| `file_mv` | `src: Str, dst: Str, byte_count: UInt32` | Performs file mv operation. |
| `file_rm` | `path: Str` | Performs file rm operation. |

## Status And Error Codes
- `STATUS_OK` (`UInt32`): `0`
- `STATUS_FILE_FAILED` (`UInt32`): `1`
- `STATUS_FILE_NOT_FOUND` (`UInt32`): `2`
- `STATUS_FILE_IO_ERROR` (`UInt32`): `3`

## Operational Constants
- `ROOT_INODE` (`UInt64`): `2`
- `DEFAULT_FILE_PERMS` (`UInt16`): `420`
- `FILE_MODE_TEXT` (`UInt32`): `1`
- `FILE_MODE_BINARY` (`UInt32`): `2`
- `O_RDONLY` (`UInt32`): `0`
- `O_WRONLY` (`UInt32`): `1`
- `O_CREAT` (`UInt32`): `64`
- `O_APPEND` (`UInt32`): `1024`
- `FILE_HANDLE_INVALID` (`UInt64`): `0`
- `FILE_OK` (`UInt32`): `0`

## Runtime Dependencies
- Detected utility/runtime call usage:
- `k_close(...)`
- `k_create(...)`
- `k_delete(...)`
- `k_open(...)`
- `k_read(...)`
- `k_write(...)`

## Integration Notes
- This module is intended for CLI and runtime utility workflows in xdvfs operations.
- It can be consumed by shell-facing command layers or higher-level orchestration utilities.

## Example (DPL)
```dust
let status = file_touch("/xdv/file");
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
