# Execute-In-Place Flash File System (XIPFS) (`fs/xipfs`)

## Overview
Implements `xipfs`, a power-fail-safe, contiguous-extent flash file system designed for direct Execute-In-Place (`XIP`) memory mapping (`mmap`) on NOR flash or block/MTD media with a four-slot ring-buffered metadata journal and online extent defragmentation.

## Interface
- `xipfs_vfs.c:g_xipfs_operations` - Global `struct mountpt_operations` table implementing `xipfs_open`, `xipfs_close`, `xipfs_read`, `xipfs_write`, `xipfs_seek`, `xipfs_ioctl`, `xipfs_mmap`, `xipfs_truncate`, `xipfs_sync`, `xipfs_dup`, `xipfs_fstat`, `xipfs_opendir`, `xipfs_closedir`, `xipfs_readdir`, `xipfs_rewinddir`, `xipfs_bind`, `xipfs_unbind`, `xipfs_statfs`, `xipfs_unlink`, `xipfs_mkdir`, `xipfs_rmdir`, `xipfs_stat`, and `xipfs_ioctldir`.
- `xipfs.h:struct xipfs_mount_s` - In-RAM mount state holding the bound driver/MTD reference, flash geometry (`geo`), XIP base pointer (`xipbase`), metadata ring state (`meta_slot`, `meta_seq`), free block bitmap (`bitmap`), staging/metadata buffers (`stage`, `metabuf`), extent list (`extents`), and recursive lock (`lock`).
- `xipfs.h:struct xipfs_extent_s` - In-RAM representation of a file or directory entry tracking its contiguous flash block run (`start_block`, `nblocks`), byte `size`, XIP mapping pin count (`pincount`), and open descriptor count (`openrefs`).
- `xipfs.h:xipfs_flash_probe`, `xipfs.h:xipfs_flash_read`, `xipfs.h:xipfs_flash_write`, `xipfs.h:xipfs_flash_erase`, `xipfs.h:xipfs_flash_addr` - Flash and block media I/O and XIP address translation (`xipfs_flash.c`).
- `xipfs.h:xipfs_meta_format`, `xipfs.h:xipfs_meta_mount`, `xipfs.h:xipfs_meta_commit`, `xipfs.h:xipfs_meta_find`, `xipfs.h:xipfs_meta_add`, `xipfs.h:xipfs_meta_detach` - Superblock and ring-buffer generation metadata management (`xipfs_meta.c`).
- `xipfs.h:xipfs_alloc_init`, `xipfs.h:xipfs_alloc_rebuild`, `xipfs.h:xipfs_alloc`, `xipfs.h:xipfs_free`, `xipfs.h:xipfs_alloc_largestrun`, `xipfs.h:xipfs_alloc_freeblocks` - Contiguous erase-block bitmap allocator (`xipfs_alloc.c`).
- `xipfs.h:xipfs_mmap` - Maps file extents directly from `xipbase` (`pincount++`) or falls back to RAM copy mapping (`xipfs_mmap.c`).
- `xipfs.h:xipfs_defrag`, `xipfs.h:xipfs_listpinned` - Relocates unpinned (`pincount == 0`) extents to coalesce free erase blocks within an optional time budget `max_ms` (`xipfs_defrag.c`).

## Invariants
- `xipfs.h:struct xipfs_dirent_s` is statically asserted (`static_assert`) to equal `XIPFS_DIRENT_SIZE` (`64` bytes) so directory entries never straddle read/write block boundaries.
- Files in `xipfs` are write-once at creation time (`ext->writing == true`) and immutable after `xipfs_close` commits the metadata generation; opening an existing file for writing without `O_TRUNC` or modifying it in place is rejected to preserve contiguous flash extents.
- `xipfs_defrag.c:xipfs_defrag` never relocates an extent whose `pincount > 0` (active XIP `mmap` alias) or `writing == true`, holding `fs->lock` across the pin check and block relocation.

## Side Effects
- Reads, writes, and erases flash blocks via MTD or block driver interfaces (`MTD_BREAD`, `MTD_BWRITE`, `MTD_ERASE`, `BIOC_XIPBASE`).
- Increments and decrements `ext->pincount` during `xipfs_mmap` and task `munmap` teardown, and allocates mount buffers (`stage`, `metabuf`, `bitmap`) and extent structures via `kmm_malloc` / `kmm_zalloc` / `kmm_free`.

## Verification
- Run: `make test`
