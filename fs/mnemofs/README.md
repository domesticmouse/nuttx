# MnemoFS NAND/NOR Flash File System

## Overview
Implements MnemoFS (`g_mnemofs_operations`), a copy-on-write flash filesystem for MTD devices utilizing Count-Trailing-Zeroes (CTZ) skip-lists for file data blocks, page/block allocation bitmaps, and checksummed directory entries.

## Interface
- `mnemofs.h:g_mnemofs_operations` - VFS mountpoint operations table (`struct mountpt_operations`) for MnemoFS.
- `mnemofs.h:struct mfs_sb_s`, `mnemofs.h:struct mfs_superblock_s`, `mnemofs.h:struct mfs_direntry_s`, `mnemofs.h:struct mfs_ofd_s` - Superblock runtime state, on-flash superblock/direntry layouts, and open file descriptors.
- `mnemofs.h:mfs_rwbuf_sync`, `mnemofs.h:mfs_rwbuf_invalidate`, `mnemofs.h:mfs_write_page`, `mnemofs.h:mfs_read_page`, `mnemofs.h:mfs_erase_blocks`, `mnemofs.h:mfs_is_bad_block` - Low-level MTD page read/write, cache buffer sync, and block erase/bad-block checks.
- `mnemofs.h:mfs_alloc_init`, `mnemofs.h:mfs_alloc_uninit`, `mnemofs.h:mfs_alloc_page`, `mnemofs.h:mfs_alloc_block`, `mnemofs.h:mfs_release_page`, `mnemofs.h:mfs_report_page_deleted`, `mnemofs.h:mfs_report_block_deleted` - Flash page and eraseblock allocator routines.
- `mnemofs.h:mfs_ctz_traverse`, `mnemofs.h:mfs_ctz_index_from_off`, `mnemofs.h:mfs_ctz_fill_next_ptrs` - CTZ skip-list traversal and pointer population.
- `mnemofs.h:mfs_dirent_traverse`, `mnemofs.h:mfs_dir_create_file`, `mnemofs.h:mfs_dir_update_file`, `mnemofs.h:mfs_dir_truncate_file`, `mnemofs.h:mfs_dir_opendir`, `mnemofs.h:mfs_dir_readdir`, `mnemofs.h:mfs_dir_unlink`, `mnemofs.h:mfs_dir_mkdir`, `mnemofs.h:mfs_dir_rmdir`, `mnemofs.h:mfs_dir_rename`, `mnemofs.h:mfs_dir_stat` - Directory traversal and namespace operations.
- `mnemofs.h:mfs_file_open`, `mnemofs.h:mfs_file_close`, `mnemofs.h:mfs_file_read`, `mnemofs.h:mfs_file_write`, `mnemofs.h:mfs_file_seek`, `mnemofs.h:mfs_file_truncate`, `mnemofs.h:mfs_file_sync`, `mnemofs.h:mfs_file_dup`, `mnemofs.h:mfs_file_fstat` - File-level VFS operations.

## Invariants
- Packed on-flash structures must preserve exact byte sizes enforced by compile-time assertions: `sizeof(struct mfs_direntry_s) == 64`, `sizeof(struct mfs_dirmeta_s) == 6`, and `sizeof(struct mfs_superblock_s) == 26` (`mnemofs.h`).
- Every VFS entry point acquires `sb->lock` via `mnemofs.c:mnemofs_lock` and flushes/invalidates the shared read/write page buffer before unlocking in `mnemofs.c:mnemofs_unlock`.

## Side Effects
- Reads, writes, and erases flash pages/blocks on the underlying MTD device (`mnemofs_rw.c`).
- Allocates superblock bitmaps (`freepages`, `delpages`), page work buffers (`rwbuf`), and open file structures (`struct mfs_ofd_s`) from kernel heap memory.

## Verification
- Run: `make test`
