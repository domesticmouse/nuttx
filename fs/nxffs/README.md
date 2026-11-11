# NuttX Flash File System (NXFFS) (`fs/nxffs`)

## Overview
Implements the NuttX wear-leveling NOR/NAND flash file system (NXFFS) atop a single Memory Technology Device (`struct mtd_dev_s`) interface, providing sequential flash block allocation, CRC-verified inode/data headers, and flash packing (garbage collection).

## Interface
- `nxffs_initialize.c:g_nxffs_operations` - Global `struct mountpt_operations` table mapping VFS calls to NXFFS handlers.
- `nxffs_initialize.c:nxffs_initialize` - Initializes and verifies the NXFFS volume on the supplied `struct mtd_dev_s` instance (`g_volume` singleton).
- `nxffs.h:struct nxffs_volume_s` - Describes the mounted NXFFS volume state, MTD device geometry, block/offset pointers, and open file list.
- `nxffs.h:nxffs_open`, `nxffs.h:nxffs_close`, `nxffs.h:nxffs_read`, `nxffs.h:nxffs_write`, `nxffs.h:nxffs_seek`, `nxffs.h:nxffs_dup`, `nxffs.h:nxffs_fstat`, `nxffs.h:nxffs_truncate` - File-level VFS operation implementations.
- `nxffs.h:nxffs_opendir`, `nxffs.h:nxffs_closedir`, `nxffs.h:nxffs_readdir`, `nxffs.h:nxffs_rewinddir` - Directory iteration operations over flat NXFFS inodes.
- `nxffs.h:nxffs_bind`, `nxffs.h:nxffs_unbind`, `nxffs.h:nxffs_statfs`, `nxffs.h:nxffs_unlink`, `nxffs.h:nxffs_stat`, `nxffs.h:nxffs_ioctl` - Mountpoint and metadata operations.
- `nxffs.h:nxffs_pack` - Compacts valid inodes and data blocks toward the beginning of flash and erases reclaimed blocks at the end.
- `nxffs.h:nxffs_reformat` - Erases and formats the entire flash volume with fresh NXFFS block headers.
- `nxffs.h:nxffs_dump` - Diagnostic utility to dump and analyze raw NXFFS flash contents.

## Invariants
- NXFFS supports only a single active volume (`g_volume` in `nxffs_initialize.c`) and a single concurrent writer (`volume->wrfile`), guarded by `volume->exclsem` (`nxmutex_lock`) and `volume->wrsem` (`nxsem_wait`).
- NXFFS does not support hierarchical subdirectories (`mkdir`/`rmdir` are NULL in `g_nxffs_operations`) or multiple simultaneous writers to different files.
- Flash headers (`struct nxffs_blkheader_s`, `struct nxffs_inode_s`, `struct nxffs_data_s`) use magic byte sequences and CRC-32 validation (`crc32`) to detect corrupt or unwritten flash regions.

## Side Effects
- Reads, writes, and erases flash memory blocks via MTD callbacks (`MTD_BREAD`, `MTD_BWRITE`, `MTD_READ`, `MTD_WRITE`, `MTD_ERASE`, `MTD_IOCTL`).
- Allocates I/O and pack buffers (`volume->cache`, `volume->pack`) and open file structures using `fs_heap_malloc` / `fs_heap_zalloc` and frees them via `fs_heap_free`.

## Verification
- Run: `make test`
