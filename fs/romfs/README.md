# Read-Only Memory File System (ROMFS) (`fs/romfs`)

## Overview
Implements the read-only `ROMFS` (ROMFSv1) filesystem on top of block drivers (including RAM disks exposing XIP memory), supporting optional in-memory node tree caching (`CONFIG_FS_ROMFS_CACHE_NODE`) and direct memory mapping (`FIOC_MMAP` / `FIOC_FILEPATH`).

## Interface
- `fs_romfs.c:g_romfs_operations` - Global `struct mountpt_operations` table implementing read-only VFS operations for ROMFS (`romfs_open`, `romfs_close`, `romfs_read`, `romfs_write` (write-back to XIP RAM disk when enabled), `romfs_seek`, `romfs_ioctl`, `romfs_dup`, `romfs_fstat`, `romfs_opendir`, `romfs_closedir`, `romfs_readdir`, `romfs_rewinddir`, `romfs_bind`, `romfs_unbind`, `romfs_statfs`, `romfs_stat`).
- `fs_romfs.h:struct romfs_mountpt_s` - Per-mountpoint state tracking the bound block driver inode, XIP base address (`rm_xipbase`), volume size, sector cache buffer (`rm_buffer`), and open file list.
- `fs_romfs.h:romfs_hwconfigure` - Queries block driver geometry and XIP capability (`BIOC_XIPBASE`) during mount.
- `fs_romfs.h:romfs_fsconfigure` - Validates the `-rom1fs-` magic header and initializes the root directory node.
- `fs_romfs.h:romfs_fileconfigure` - Allocates and populates the per-file sector cache (`rf_buffer`) upon opening a file.
- `fs_romfs.h:romfs_hwread` - Reads sectors from the underlying block driver or directly from `rm_xipbase` if XIP is active.
- `fs_romfs.h:romfs_filecacheread` - Reads sectors into a file's private sector cache (`rf_buffer`).
- `fs_romfs.h:romfs_checkmount` - Verifies that the underlying media is still present and mounted.
- `fs_romfs.h:romfs_finddirentry`, `fs_romfs.h:romfs_parsedirentry`, `fs_romfs.h:romfs_parsefilename`, `fs_romfs.h:romfs_datastart`, `fs_romfs.h:romfs_freenode` - Internal ROMFS header and directory traversal utilities.

## Invariants
- A valid ROMFS image must start with the 8-byte magic string `"-rom1fs-"` (`ROMFS_VMAGIC` in `fs_romfs.h`).
- Concurrent access to the shared mountpoint sector cache (`rm_buffer`) and open file list (`rm_head`) is serialized via `rm_lock` (`nxrmutex_lock`).
- `fs_romfs.c:romfs_unbind` fails with `-EBUSY` if `rm->rm_head` is non-NULL (open files exist).

## Side Effects
- Performs sector reads (and optional XIP writes via `romfs_hwxipwrite`) on the bound block driver (`rm_blkdriver->u.i_bops->read`, `ioctl`).
- Allocates mountpoint structures, sector caches, open file descriptors, and optional cached directory trees (`struct romfs_nodeinfo_s`) from the filesystem heap (`fs_heap_malloc`, `fs_heap_zalloc`, `fs_heap_free`).

## Verification
- Run: `make test`
