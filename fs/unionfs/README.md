# Union File System (`fs/unionfs`)

## Overview
Implements a union overlay filesystem (`unionfs`) that merges two existing mounted filesystems (`ui_fs[0]` and `ui_fs[1]`) with optional path prefixes into a single unified namespace, giving precedence to file system 1 while falling back to file system 2.

## Interface
- `fs_unionfs.c:g_unionfs_operations` - Global `struct mountpt_operations` table implementing `unionfs_open`, `unionfs_close`, `unionfs_read`, `unionfs_write`, `unionfs_seek`, `unionfs_ioctl`, `unionfs_truncate`, `unionfs_sync`, `unionfs_dup`, `unionfs_fstat`, `unionfs_fchstat`, `unionfs_opendir`, `unionfs_closedir`, `unionfs_readdir`, `unionfs_rewinddir`, `unionfs_bind`, `unionfs_unbind`, `unionfs_statfs`, `unionfs_unlink`, `unionfs_mkdir`, `unionfs_rmdir`, `unionfs_rename`, `unionfs_stat`, and `unionfs_chstat`.
- `fs_unionfs.c:struct unionfs_inode_s` - Per-mountpoint state holding the two contained child mountpoints (`ui_fs[2]`), mutual exclusion lock (`ui_lock`), open file count (`ui_nopen`), and unmount state (`ui_unmounted`).
- `fs_unionfs.c:struct unionfs_mountpt_s` - Associates a child mountpoint inode (`um_node`) with its configured path prefix (`um_prefix`).

## Invariants
- `fs_unionfs.c:unionfs_bind` requires a mount option string (`data`) specifying two valid, already-mounted filesystem paths (`fspath1` and `fspath2`), detaching both child mountpoint inodes from the global VFS tree so they are exclusively owned by the unionfs mountpoint.
- `fs_unionfs.c:unionfs_open` always attempts to open existing files on `ui_fs[0]` before `ui_fs[1]`, and when creating a new file (`O_CREAT`), supports copy-on-write / fallback creation across the two underlying filesystems.

## Side Effects
- Removes the two target mountpoint inodes from the VFS namespace (`inode_remove`) during `unionfs_dobind` and destroys/unbinds both underlying filesystems (`unionfs_unbind_child`) when the unionfs mountpoint is unmounted and all open files close.
- Allocates unionfs mount state, path buffers, directory iterators, and open file wrappers on the filesystem heap (`fs_heap_zalloc`, `fs_heap_strdup`, `fs_heap_free`).

## Verification
- Run: `make test`
