# Sector Map Allocation for Really Tiny (SMART) Flash File System (`fs/smartfs`)

## Overview
Implements the hierarchical SMART flash file system (`smartfs`) on top of the SMART MTD block driver (`nuttx/fs/smart.h`), chaining logical flash sectors (`struct smartfs_chain_header_s`) to store directories and files with optional sector buffering and CRC validation.

## Interface
- `smartfs_smart.c:g_smartfs_operations` - Global `struct mountpt_operations` table implementing VFS operations for SMARTFS (`smartfs_open`, `smartfs_close`, `smartfs_read`, `smartfs_write`, `smartfs_seek`, `smartfs_ioctl`, `smartfs_truncate`, `smartfs_sync`, `smartfs_dup`, `smartfs_fstat`, `smartfs_opendir`, `smartfs_closedir`, `smartfs_readdir`, `smartfs_rewinddir`, `smartfs_bind`, `smartfs_unbind`, `smartfs_statfs`, `smartfs_unlink`, `smartfs_mkdir`, `smartfs_rmdir`, `smartfs_rename`, `smartfs_stat`).
- `smartfs.h:struct smartfs_mountpt_s` - Per-mountpoint state tracking the underlying SMART block driver (`fs_blkdriver`), open file list (`fs_head`), low-level format geometry (`fs_llformat`), working buffers (`fs_rwbuffer`, `fs_workbuffer`), and root sector number (`fs_rootsector`).
- `smartfs.h:smartfs_mount`, `smartfs.h:smartfs_unmount` - Mounts and unmounts a SMARTFS volume, initializing low-level format state and shared sector buffers.
- `smartfs.h:smartfs_finddirentry`, `smartfs.h:smartfs_createentry`, `smartfs.h:smartfs_deleteentry`, `smartfs.h:smartfs_countdirentries` - Directory sector chain search, creation, deletion, and entry counting utilities.
- `smartfs.h:smartfs_sync_internal`, `smartfs.h:smartfs_seek_internal`, `smartfs.h:smartfs_shrinkfile`, `smartfs.h:smartfs_extendfile` - File sector chain flushing, seeking, and truncation helpers.
- `smartfs.h:smartfs_get_first_mount` - Returns the head of the mounted SMARTFS volume list for `procfs` inspection (`smartfs_procfs.c`).

## Invariants
- All SMARTFS mountpoint and file operations serialize access through the global mutex `g_lock` (`nxmutex_lock` in `smartfs_smart.c`).
- Root directory traversal begins at logical sector `SMARTFS_ROOT_DIR_SECTOR` (`3`, or offset by root directory index when `CONFIG_SMARTFS_MULTI_ROOT_DIRS` is enabled).
- `smartfs_smart.c:smartfs_unbind` returns `-EBUSY` if `fs->fs_head != NULL` (any files remain open).

## Side Effects
- Issues SMART block driver `ioctl` commands (`BIOC_GETFORMAT`, `BIOC_ALLOCSECT`, `BIOC_FREESECT`, `BIOC_READSECT`, `BIOC_WRITESECT`) via `FS_IOCTL` to read, write, allocate, and release logical flash sectors.
- Allocates mountpoint state, sector read/write buffers, and open file descriptors on the filesystem heap (`fs_heap_malloc`, `fs_heap_zalloc`, `fs_heap_free`).

## Verification
- Run: `make test`
