# SPIFFS Core and VFS Implementation

## Overview
Implements the SPI Flash File System (SPIFFS) volume management, page caching, garbage collection, consistency checking, MTD flash translation, and NuttX VFS mountpoint operations for wear-leveled NOR flash storage.

## Interface
- `spiffs_vfs.c:g_spiffs_operations` - VFS mountpoint operations table (`struct mountpt_operations`) for SPIFFS volumes.
- `spiffs.h:struct spiffs_s`, `spiffs.h:struct spiffs_file_s` - Volume state and open file object representations.
- `spiffs.h:spiffs_stat_pgndx`, `spiffs.h:spiffs_find_fobj_bypgndx`, `spiffs.h:spiffs_find_fobj_byobjid`, `spiffs.h:spiffs_fobj_flush`, `spiffs.h:spiffs_fobj_write`, `spiffs.h:spiffs_fobj_read`, `spiffs.h:spiffs_fobj_free` - File object lookup, read/write, flush, and release operations.
- `spiffs_core.h:spiffs_objlu_scan`, `spiffs_core.h:spiffs_fobj_create`, `spiffs_core.h:spiffs_fobj_open_bypage`, `spiffs_core.h:spiffs_fobj_append`, `spiffs_core.h:spiffs_fobj_modify`, `spiffs_core.h:spiffs_fobj_truncate`, `spiffs_core.h:spiffs_object_read`, `spiffs_core.h:spiffs_erase_block` - Core object lookup table (OBJLU) and page/index manipulation routines.
- `spiffs_cache.h:spiffs_cache_initialize`, `spiffs_cache.h:spiffs_cache_read`, `spiffs_cache.h:spiffs_cache_write`, `spiffs_cache.h:spiffs_cache_drop_page`, `spiffs_cache.h:spiffs_cache_page_get_byobjid`, `spiffs_cache.h:spiffs_cache_page_allocate_byobjid`, `spiffs_cache.h:spiffs_cache_page_release` - Read/write page cache management.
- `spiffs_gc.h:spiffs_gc_quick`, `spiffs_gc.h:spiffs_gc_check` - Garbage collection routines for reclaiming deleted flash pages and blocks.
- `spiffs_check.h:spiffs_check_luconsistency`, `spiffs_check.h:spiffs_check_pgconsistency`, `spiffs_check.h:spiffs_check_objidconsistency`, `spiffs_check.h:spiffs_dump` - Flash lookup, page, and object index consistency checkers.
- `spiffs_mtd.h:spiffs_mtd_write`, `spiffs_mtd.h:spiffs_mtd_read`, `spiffs_mtd.h:spiffs_mtd_erase` - MTD hardware abstraction wrappers.

## Invariants
- `spiffs_vfs.c:spiffs_lock_volume` (`spiffs.h:struct spiffs_s` `lock`) must be held across volume state, cache, and object queue (`objq`) operations to maintain thread-safe access.
- Flash block size must be an integer multiple of page size (`spiffs_core.h:SPIFFS_GEO_PAGES_PER_BLOCK`), and NOR flash bits can only transition from `1` to `0` without an explicit block erase (`spiffs_core.h:spiffs_erase_block`).
- Internal error codes below `spiffs_core.h:SPIFFS_ERR_INTERNAL` must be mapped to standard POSIX negated errno values via `spiffs_vfs.c:spiffs_map_errno` before returning to VFS callers.

## Side Effects
- Performs NOR flash read, write, and block erase I/O via the underlying MTD device (`spiffs_mtd.h:spiffs_mtd_read`, `spiffs_mtd.h:spiffs_mtd_write`, `spiffs_mtd.h:spiffs_mtd_erase`).
- Allocates and frees volume work buffers, cache pages, and file objects from the filesystem heap (`spiffs_vfs.c:spiffs_bind`, `spiffs.h:spiffs_fobj_free`).
- Mutates in-memory page caches (`spiffs_cache.h:struct spiffs_cache_s`) and open file object lists (`spiffs.h:struct spiffs_s`).

## Verification
- Run: `make test`
