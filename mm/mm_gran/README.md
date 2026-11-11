# mm_gran

## Overview
Fixed-size granule and physical page memory allocator (`CONFIG_GRAN` and `CONFIG_MM_PGALLOC`). Manages contiguous regions of memory in power-of-two granules (`1 << log2gran`) using a compact bit-mapped Granule Allocation Table (`gat` in `struct gran_s`), suitable for DMA buffers, aligned hardware memory pools, and MMU physical page allocation.

## Interface
- `[mm_gran.h:struct gran_s]`, `[mm_grantable.h:struct gran_range_s]`, `[mm_grantable.h:gatr_t]`, `[mm_grantable.h:gran_t]`
- `[mm_graninit.c:gran_initialize]`, `[mm_granrelease.c:gran_release]`
- `[mm_granalloc.c:gran_alloc]`, `[mm_granalloc.c:gran_alloc_align]`, `[mm_granfree.c:gran_free]`, `[mm_granreserve.c:gran_reserve]`
- `[mm_graninfo.c:gran_info]`, `[mm_grancritical.c:gran_enter_critical]`, `[mm_grancritical.c:gran_leave_critical]`
- `[mm_grantable.c:gran_range]`, `[mm_grantable.c:gran_match]`, `[mm_grantable.c:gran_search]`, `[mm_grantable.c:gran_set]`, `[mm_grantable.c:gran_clear]`
- `[mm_pgalloc.c:mm_pginitialize]`, `[mm_pgalloc.c:mm_pgreserve]`, `[mm_pgalloc.c:mm_pgalloc]`, `[mm_pgalloc.c:mm_pgalloc_align]`, `[mm_pgalloc.c:mm_pgfree]`, `[mm_pgalloc.c:mm_pginfo]`

## Invariants
- `log2gran` must be in `(0, 32)` and `log2gran >= log2align` so every contiguous granule boundary satisfies the minimum alignment (`[mm_graninit.c:gran_initialize]`).
- `lowfree` in `[mm_gran.h:struct gran_s]` is always less than or equal to the index of the lowest free granule in `gat` (`[mm_grantable.c:gran_search]`, `[mm_grantable.c:gran_set]`, `[mm_grantable.c:gran_clear]`).
- Any memory range passed to `[mm_granfree.c:gran_free]` must be aligned to `1 << log2align`, lie within `[heapstart, GRANENDA)`, and have all corresponding bits in `gat` currently marked allocated (`[mm_granfree.c:gran_free]`).

## Side Effects
- Allocates and frees the `struct gran_s` descriptor and GAT bitmap from the kernel heap via `kmm_zalloc` and `kmm_free` (`[mm_graninit.c:gran_initialize]`, `[mm_granrelease.c:gran_release]`).
- Synchronizes access to the GAT bitmap using either an interrupt-saving spinlock (`spin_lock_irqsave` when `CONFIG_GRAN_INTR` is enabled) or a kernel mutex (`nxmutex_lock`) (`[mm_grancritical.c:gran_enter_critical]`).
- Mutates the static page allocator handle `g_pgalloc` when `CONFIG_MM_PGALLOC` is enabled (`[mm_pgalloc.c:mm_pginitialize]`).

## Verification
- Run: `make test`
