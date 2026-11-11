# tlsf

## Overview
Two-Level Segregated Fit (TLSF) O(1) heap memory allocator backend (`CONFIG_MM_TLSF_MANAGER`). Implements the standard NuttX `mm_*` heap interface (`struct mm_heap_s`) on top of an external TLSF pool engine (`tlsf_t`), supporting multiple regions, per-CPU delayed free lists, optional multi-pool small-block caching (`CONFIG_MM_HEAP_MEMPOOL`), KASan poisoning, and trailing allocation backtrace metadata.

## Interface
- `[mm_tlsf.c:struct mm_heap_s]`
- `[mm_tlsf.c:mm_initialize_heap]`, `[mm_tlsf.c:mm_initialize_pool]`, `[mm_tlsf.c:mm_addregion]`, `[mm_tlsf.c:mm_uninitialize]`
- `[mm_tlsf.c:mm_malloc]`, `[mm_tlsf.c:mm_free]`, `[mm_tlsf.c:mm_realloc]`, `[mm_tlsf.c:mm_memalign]`, `[mm_tlsf.c:mm_calloc]`, `[mm_tlsf.c:mm_zalloc]`
- `[mm_tlsf.c:mm_malloc_size]`, `[mm_tlsf.c:mm_heapmember]`, `[mm_tlsf.c:mm_brkaddr]`, `[mm_tlsf.c:mm_extend]`
- `[mm_tlsf.c:mm_mallinfo]`, `[mm_tlsf.c:mm_mallinfo_task]`, `[mm_tlsf.c:mm_heapfree]`, `[mm_tlsf.c:mm_heapfree_largest]`
- `[mm_tlsf.c:mm_checkcorruption]`, `[mm_tlsf.c:mm_memdump]`

## Invariants
- Initial heap size passed to `[mm_tlsf.c:mm_initialize_heap]` must exceed `sizeof(struct mm_heap_s) + tlsf_size()`.
- Region extensions via `[mm_tlsf.c:mm_extend]` require `mem == heap->mm_heapend[region]` so the TLSF pool grows contiguously.
- When `CONFIG_MM_BACKTRACE >= 0`, every TLSF allocation appends `sizeof(struct memdump_backtrace_s)` bytes to the end of the block, which `[mm_tlsf.c:mm_malloc_size]` subtracts from `tlsf_block_size(mem)`.

## Side Effects
- Mutates TLSF control structures and pool headers under `heap->mm_lock` mutex protection or interrupt masking for per-CPU `mm_delaylist` queues (`[mm_tlsf.c:mm_malloc]`, `[mm_tlsf.c:mm_free]`).
- Registers/unregisters regions and poisons/unpoisons blocks with KASan (`[mm_tlsf.c:mm_addregion]`, `[mm_tlsf.c:mm_malloc]`, `[mm_tlsf.c:mm_delayfree]`).
- Emits scheduler heap instrumentation notes (`sched_note_heap`), registers procfs meminfo entries (`procfs_register_meminfo`), and logs memory dumps via `syslog` (`[mm_tlsf.c:mm_memdump]`).

## Verification
- Run: `make test`
