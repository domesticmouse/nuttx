# Temporary RAM File System (TMPFS) (`fs/tmpfs`)

## Overview
Implements an in-memory, volatile RAM filesystem (`tmpfs`) storing directories (`struct tmpfs_directory_s`) and regular files (`struct tmpfs_file_s`) as dynamically reallocated memory objects with direct memory mapping (`mmap`) support.

## Interface
- `fs_tmpfs.c:g_tmpfs_operations` - Global `struct mountpt_operations` table implementing `tmpfs_open`, `tmpfs_close`, `tmpfs_read`, `tmpfs_write`, `tmpfs_seek`, `tmpfs_ioctl`, `tmpfs_mmap`, `tmpfs_truncate`, `tmpfs_sync`, `tmpfs_dup`, `tmpfs_fstat`, `tmpfs_fchstat`, `tmpfs_opendir`, `tmpfs_closedir`, `tmpfs_readdir`, `tmpfs_rewinddir`, `tmpfs_bind`, `tmpfs_unbind`, `tmpfs_statfs`, `tmpfs_unlink`, `tmpfs_mkdir`, `tmpfs_rmdir`, `tmpfs_rename`, `tmpfs_stat`, `tmpfs_chstat`, and `tmpfs_permission`.
- `fs_tmpfs.h:struct tmpfs_s` - Represents a mounted TMPFS instance holding the root directory entry (`tfs_root`) and recursive mount lock (`tfs_lock`).
- `fs_tmpfs.h:struct tmpfs_object_s`, `fs_tmpfs.h:struct tmpfs_directory_s`, `fs_tmpfs.h:struct tmpfs_file_s` - Common header, directory object, and file object structures sharing an identical prefix layout (`to_lock`, `to_alloc`, `to_type`, `to_refs`, `to_parent`, `to_ino`).
- `fs_tmpfs.h:enum tmpfs_objtype_e` - Object type discriminator (`TMPFS_DIRECTORY`, `TMPFS_REGULAR`).

## Invariants
- `struct tmpfs_directory_s` and `struct tmpfs_file_s` must maintain identical initial fields matching `struct tmpfs_object_s` so pointers can be safely cast between generic objects and specific types.
- `CONFIG_FS_TMPFS_DIRECTORY_FREEGUARD` must be strictly greater than `CONFIG_FS_TMPFS_DIRECTORY_ALLOCGUARD`, and `CONFIG_FS_TMPFS_FILE_FREEGUARD` must be strictly greater than `CONFIG_FS_TMPFS_FILE_ALLOCGUARD` to prevent thrashing during reallocation.
- Unlinked file objects (`TFO_FLAG_UNLINKED`) remain allocated until their reference count (`tfo_refs`) drops to zero upon final `tmpfs_close`.

## Side Effects
- Allocates, reallocates, and frees directory and file backing buffers from the filesystem heap (`fs_heap_malloc`, `fs_heap_zalloc`, `fs_heap_realloc`, `fs_heap_free`).
- Acquires recursive mutexes (`tfs_lock`, `to_lock`, `tfo_lock`, `tdo_lock`) and increments the global atomic inode serial counter `g_tmpfs_ino`.

## Verification
- Run: `make test`
