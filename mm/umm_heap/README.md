# umm_heap

## Overview
User-space and standard C library heap allocator frontend (`USR_HEAP` / `g_mmheap`). Implements standard POSIX/C allocation functions (`malloc`, `free`, `realloc`, `memalign`, `calloc`, `zalloc`, `sbrk`, `mallinfo`, `malloc_size`) and `umm_*` management wrappers on top of the core `mm_*` heap engine, supporting dynamic page-backed heap growth via `pgalloc` and `sbrk` in `CONFIG_BUILD_KERNEL` address environments.

## Interface
- `[umm_globals.c:g_mmheap]`, `[umm_memdump.c:g_mm_seqno]`
- `[umm_initialize.c:umm_initialize]`, `[umm_initialize.c:umm_try_initialize]`
- `[umm_addregion.c:umm_addregion]`, `[umm_extend.c:umm_extend]`, `[umm_brkaddr.c:umm_brkaddr]`, `[umm_sbrk.c:sbrk]`
- `[umm_malloc.c:malloc]`, `[umm_free.c:free]`, `[umm_realloc.c:realloc]`, `[umm_memalign.c:memalign]`, `[umm_calloc.c:calloc]`, `[umm_zalloc.c:zalloc]`
- `[umm_malloc_size.c:malloc_size]`, `[umm_heapmember.c:umm_heapmember]`
- `[umm_mallinfo.c:mallinfo]`, `[umm_mallinfo.c:mallinfo_task]`, `[umm_checkcorruption.c:umm_checkcorruption]`, `[umm_memdump.c:umm_memdump]`

## Invariants
- `[umm_sbrk.c:sbrk]` only supports non-negative increments (`incr >= 0`); negative increments fail with `ENOSYS`.
- In `CONFIG_BUILD_KERNEL`, `[umm_initialize.c:umm_try_initialize]` ensures `USR_HEAP` is lazily initialized via `pgalloc(0, npages)` before any user allocation or `sbrk` operation proceeds (`[umm_sbrk.c:sbrk]`, `[umm_memalign.c:memalign]`, `[umm_realloc.c:realloc]`).
- `[umm_calloc.c:calloc]` verifies `elem_size == 0 || n <= (SIZE_MAX / elem_size)` before multiplying to prevent integer overflow.

## Side Effects
- Mutates `USR_HEAP` (`[umm_globals.c:g_mmheap]`), requests virtual/physical pages via `pgalloc` in `[umm_sbrk.c:sbrk]` and `[umm_initialize.c:umm_try_initialize]`, and extends region 0 via `mm_extend`.
- Sets thread-local `errno` (`ENOMEM`, `EAGAIN`, `ENOSYS`) via `[umm_heap.h:umm_set_errno]` when compiled for flat or user-space builds, and notifies memory pressure listeners via `mm_notify_pressure` (`[umm_malloc.c:malloc]`, `[umm_realloc.c:realloc]`, `[umm_memalign.c:memalign]`).

## Verification
- Run: `make test`
