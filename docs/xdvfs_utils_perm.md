# XdvFsUtilsPerm

- Source: `xdv-xdvfs-utils/src/xdvfs_utils_perm.ds`
- Summary: xdv-xdvfs-utils: permissions/ownership workflows

## Purpose
xdv-xdvfs-utils: permissions/ownership workflows

## Public Procedures
| Procedure | Parameters | Description |
|---|---|---|
| `perm_chmod` | `path: Str, mode: UInt16` | Performs perm chmod operation. |
| `perm_chown` | `path: Str, user_id: UInt32` | Performs perm chown operation. |
| `perm_chgrp` | `path: Str, group_id: UInt32` | Performs perm chgrp operation. |
| `perm_set_umask` | `mask: UInt16` | Performs perm set umask operation. |
| `perm_default_umask` | `(none)` | Performs perm default umask operation. |

## Status And Error Codes
- `STATUS_OK` (`UInt32`): `0`
- `STATUS_PERM_FAILED` (`UInt32`): `1`
- `STATUS_PATH_NOT_FOUND` (`UInt32`): `2`
- `STATUS_INVALID_MODE` (`UInt32`): `3`

## Operational Constants
- `ROOT_INODE` (`UInt64`): `2`
- `DEFAULT_UMASK` (`UInt16`): `18`
- `MAX_MODE` (`UInt16`): `511`

## Runtime Dependencies
- Detected utility/runtime call usage:
- `get_inode(...)`
- `lookup(...)`
- `write_inode(...)`

## Integration Notes
- This module is intended for CLI and runtime utility workflows in xdvfs operations.
- It can be consumed by shell-facing command layers or higher-level orchestration utilities.

## Example (DPL)
```dust
let status = perm_chmod("/xdv/file", 420);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
