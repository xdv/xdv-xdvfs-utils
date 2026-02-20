# XdvFsUtilsDir

- Source: `xdv-xdvfs-utils/src/xdvfs_utils_dir.ds`
- Summary: xdv-xdvfs-utils: directory workflows

## Purpose
xdv-xdvfs-utils: directory workflows

## Public Procedures
| Procedure | Parameters | Description |
|---|---|---|
| `dir_mkdir` | `name: Str` | Performs dir mkdir operation. |
| `dir_mkdir_mode` | `name: Str, perms: UInt16` | Performs dir mkdir mode operation. |
| `dir_ls` | `path: Str, flags: UInt32` | Performs dir ls operation. |
| `dir_tree` | `path: Str` | Performs dir tree operation. |
| `dir_rm` | `name: Str` | Performs dir rm operation. |
| `dir_mv` | `old_name: Str, new_name: Str` | Performs dir mv operation. |

## Status And Error Codes
- `STATUS_OK` (`UInt32`): `0`
- `STATUS_DIR_FAILED` (`UInt32`): `1`
- `STATUS_DIR_NOT_FOUND` (`UInt32`): `2`

## Operational Constants
- `ROOT_INODE` (`UInt64`): `2`
- `DEFAULT_DIR_PERMS` (`UInt16`): `493`
- `LIST_RECURSIVE` (`UInt32`): `1`
- `DEFAULT_TREE_DEPTH` (`UInt32`): `8`
- `DIR_ENTRY_NOT_FOUND` (`UInt64`): `0`
- `DIR_OK` (`UInt32`): `0`

## Runtime Dependencies
- Detected utility/runtime call usage:
- `add_dir_entry(...)`
- `closedir(...)`
- `lookup(...)`
- `mkdir(...)`
- `opendir(...)`
- `readdir(...)`
- `remove_dir_entry(...)`
- `rmdir(...)`

## Integration Notes
- This module is intended for CLI and runtime utility workflows in xdvfs operations.
- It can be consumed by shell-facing command layers or higher-level orchestration utilities.

## Example (DPL)
```dust
let status = dir_mkdir("sample");
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
