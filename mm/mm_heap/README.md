# mm_heap

## Overview
Core multi-instance heap memory allocator for NuttX (`struct mm_heap_s`). Implements best-fit chunk allocation over power-of-two size-indexed doubly linked free lists (`mm_nodelist`), supporting multiple non-contiguous memory regions, delayed deallocation (`mm_delaylist`) for interrupt/context-switch contexts, optional multi-bin memory pool frontends (`CONFIG_MM_HEAP_MEMPOOL`), KASan instrumentation, and allocation backtrace tracking.

## Interface
- `[mm.h:struct mm_heap_s]`, `[mm.h:struct mm_allocnode_s]`, `[mm.h:struct mm_freenode_s]`, `[mm.h:mm_node_handler_t]`
- `[mm_initialize.c:mm_initialize_heap]`, `[mm_initialize.c:mm_initialize_pool]`, `[mm_initialize.c:mm_addregion]`, `[mm_initialize.c:mm_uninitialize]`
- `[mm_malloc.c:mm_malloc]`, `[mm_malloc.c:mm_free_delaylist]`, `[mm_free.c:mm_free]`, `[mm_free.c:mm_delayfree]`
- `[mm_realloc.c:mm_realloc]`, `[mm_memalign.c:mm_memalign]`, `[mm_calloc.c:mm_calloc]`, `[mm_zalloc.c:mm_zalloc]`
- `[mm_malloc_size.c:mm_malloc_size]`, `[mm_heapmember.c:mm_heapmember]`, `[mm_brkaddr.c:mm_brkaddr]`, `[mm_extend.c:mm_extend]`
- `[mm_mallinfo.c:mm_mallinfo]`, `[mm_mallinfo.c:mm_mallinfo_task]`, `[mm_mallinfo.c:mm_heapfree]`, `[mm_mallinfo.c:mm_heapfree_largest]`
- `[mm_foreach.c:mm_foreach]`, `[mm_checkcorruption.c:mm_checkcorruption]`, `[mm_memdump.c:mm_memdump]`
- `[mm_lock.c:mm_lock]`, `[mm_lock.c:mm_unlock]`, `[mm_lock.c:mm_lock_irq]`, `[mm_lock.c:mm_unlock_irq]`
- `[mm_shrinkchunk.c:mm_shrinkchunk]`, `[mm.h:mm_addfreechunk]`

## Invariants
- Every heap region is bounded by two permanently allocated guard nodes (`[mm.h:mm_heapstart]` and `[mm.h:mm_heapend]`) marked with `[mm.h:MM_ALLOC_BIT]` to prevent coalescing past region boundaries (`[mm_initialize.c:mm_addregion]`).
- Chunk sizes are aligned to `MM_ALIGN`, leaving the two lowest bits of `size` to encode `[mm.h:MM_ALLOC_BIT]` and `[mm.h:MM_PREVFREE_BIT]`; physical chunks must be at least `[mm.h:MM_MIN_CHUNK]` bytes (`[mm.h:MM_SIZEOF_NODE]`).
- Free chunks in `[mm.h:mm_nodelist]` are ordered by ascending chunk size within each log2 bucket (`[mm.h:mm_addfreechunk]`, `[mm_checkcorruption.c:mm_checkcorruption]`), and two physically adjacent free chunks are always coalesced immediately upon deallocation (`[mm_free.c:mm_delayfree]`).
- Extending a heap region via `[mm_extend.c:mm_extend]` requires the new block to immediately follow the existing `mm_heapend[region]` guard node and be aligned to `MM_ALIGN`.

## Side Effects
- Mutates heap nodelists, allocation headers, and usage metrics under mutex protection (`[mm_lock.c:mm_lock]`, `[mm.h:mm_lock]`) or interrupt masking for per-CPU delay lists (`[mm_lock.c:mm_lock_irq]`, `[mm.h:mm_delaylist]`).
- Registers/unregisters regions and poisons/unpoisons chunks via KASan hooks (`[mm_initialize.c:mm_addregion]`, `[mm_malloc.c:mm_malloc]`, `[mm_free.c:mm_delayfree]`).
- Emits scheduler heap trace notes (`sched_note_heap`), procfs meminfo entries (`procfs_register_meminfo`), and syslog diagnostic dumps (`[mm_memdump.c:mm_memdump]`).

## Verification
- Run: `make test`
