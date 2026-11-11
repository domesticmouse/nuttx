# FAT12/FAT16/FAT32 File System

## Overview
Implements the FAT12, FAT16, and FAT32 filesystem driver (`g_fat_operations`), supporting short 8.3 and optional VFAT long filenames (`CONFIG_FAT_LFN`), cluster chain management, sector caching, FSINFO sector updates, and POSIX open-file unlink/rename semantics via shared open-file objects.

## Interface
- `fs_fat32.c:g_fat_operations` - VFS mountpoint operations table (`struct mountpt_operations`) for FAT volumes.
- `fs_fat32.h:struct fat_mountpt_s`, `fs_fat32.h:struct fat_shared_s`, `fs_fat32.h:struct fat_file_s`, `fs_fat32.h:struct fat_dirinfo_s` - Mountpoint state, shared canonical open-file state, per-handle file descriptor state, and directory traversal structures.
- `fs_fat32.h:fat_mount`, `fs_fat32.h:fat_checkmount`, `fs_fat32.h:fat_hwread`, `fs_fat32.h:fat_hwwrite` - Volume boot record parsing, mount verification, and sector I/O helpers.
- `fs_fat32.h:fat_cluster2sector`, `fs_fat32.h:fat_getcluster`, `fs_fat32.h:fat_putcluster`, `fs_fat32.h:fat_removechain`, `fs_fat32.h:fat_extendchain` - FAT table and cluster chain manipulation.
- `fs_fat32.h:fat_finddirentry`, `fs_fat32.h:fat_nextdirentry`, `fs_fat32.h:fat_allocatedirentry`, `fs_fat32.h:fat_freedirentry`, `fs_fat32.h:fat_dircreate`, `fs_fat32.h:fat_remove`, `fs_fat32.h:fat_dirtruncate`, `fs_fat32.h:fat_dirshrink`, `fs_fat32.h:fat_dirextend` - Directory entry lookup, creation, removal, and file size adjustment.
- `fs_fat32.h:fat_fscacheflush`, `fs_fat32.h:fat_fscacheread`, `fs_fat32.h:fat_ffcacheflush`, `fs_fat32.h:fat_ffcacheread`, `fs_fat32.h:fat_ffcacheinvalidate`, `fs_fat32.h:fat_updatefsinfo` - Volume and file sector cache management.
- `fs_fat32attrib.c:fat_getattrib`, `fs_fat32attrib.c:fat_setattrib` - FAT file attribute getter and setter interfaces.

## Invariants
- All mountpoint state, FAT table updates, and shared file list (`fs_shared`, `fs_head`) mutations must hold `fs->fs_lock` (`fs_fat32.h:struct fat_mountpt_s`).
- Every open handle for the same on-disk file shares a single `fs_fat32.h:struct fat_shared_s` instance; unlinked open files set `s_pending = true` and defer cluster chain reclamation until `s_refs` drops to zero (`fs_fat32.c:fat_shared_release`).
- Before shrinking or truncating a cluster chain, all per-handle sector caches attached to the shared file must be flushed/invalidated (`fs_fat32.c:fat_shared_invalidate`).

## Side Effects
- Reads and writes sectors on the backing block device via `fs_fat32.h:fat_hwread` and `fs_fat32.h:fat_hwwrite`.
- Allocates sector buffers from either the filesystem heap or architecture DMA memory (`fs_fat32.h:fat_io_alloc`, `fs_fat32.h:fat_io_free`).

## Verification
- Run: `make test`
