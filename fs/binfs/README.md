# Built-In Application File System (BINFS)

## Overview
Provides a read-only pseudo-filesystem (`CONFIG_FS_BINFS`) that exposes NuttX built-in applications (registered in the builtin application table) as executable directory entries under a mounted path such as `/bin`.

## Interface
- `fs_binfs.c:g_binfs_operations` - VFS mountpoint operations table (`struct mountpt_operations`) implementing read-only file and directory lookups for built-in applications.

## Invariants
- All open requests must specify `O_RDONLY` (`fs_binfs.c:binfs_open`); any write mode is rejected with `-EACCES`.
- Only valid built-in application indices verified via `builtin_isavail` are stored in `filep->f_priv` (`fs_binfs.c:binfs_open`).

## Side Effects
- Allocates and frees directory iteration state (`fs_binfs.c:struct binfs_dir_s`) via `fs_heap_zalloc` and `fs_heap_free` during `fs_binfs.c:binfs_opendir` and `fs_binfs.c:binfs_closedir`.

## Verification
- Run: `make test`
