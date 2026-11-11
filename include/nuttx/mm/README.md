# Memory Management (`include/nuttx/mm`)

## Overview
Defines the core memory management subsystems in NuttX, including the granule allocator (`gran.h`), I/O buffer (IOB) chains and queues (`iob.h`), Kernel Address Sanitizer instrumentation (`kasan.h`), dynamic kernel virtual page mapping (`kmap.h`), per-process virtual memory mapping tracking (`map.h`), fixed-block and multi-pool memory allocators (`mempool.h`), and the general heap allocator (`mm.h`).

## Interface
- `mm.h:struct mm_heap_s`, `mm.h:struct mm_heap_config_s`, `mm.h:struct mempool_init_s`, `mm.h:g_mmheap`, `mm.h:USR_HEAP`, `mm.h:KRN_HEAP`, `mm.h:mm_extend`, `mm.h:umm_extend`, `mm.h:kmm_extend`, `mm.h:mm_mallinfo`, `mm.h:mm_mallinfo_task`, `mm.h:mm_heapfree`, `mm.h:mm_heapfree_largest`, `mm.h:mm_memdump`, `mm.h:umm_memdump`, `mm.h:mm_checkcorruption`, `mm.h:mm_notify_pressure`
- `gran.h:GRAN_HANDLE`, `gran.h:struct graninfo_s`, `gran.h:gran_initialize`, `gran.h:gran_release`, `gran.h:gran_reserve`, `gran.h:gran_alloc`, `gran.h:gran_alloc_align`, `gran.h:gran_free`, `gran.h:gran_info`
- `iob.h:struct iob_s`, `iob.h:struct iob_qentry_s`, `iob.h:struct iob_queue_s`, `iob.h:struct iob_stats_s`, `iob.h:iob_initialize`, `iob.h:iob_alloc`, `iob.h:iob_timedalloc`, `iob.h:iob_tryalloc`, `iob.h:iob_free`, `iob.h:iob_free_chain`, `iob.h:iob_add_queue`, `iob.h:iob_clone`, `iob.h:iob_concat`, `iob.h:iob_trimhead`, `iob.h:iob_trimtail`, `iob.h:iob_pack`, `iob.h:iob_contig`
- `kasan.h:kasan_poison`, `kasan.h:kasan_unpoison`, `kasan.h:kasan_register`, `kasan.h:kasan_unregister`, `kasan.h:kasan_set_tag`, `kasan.h:kasan_clear_tag`, `kasan.h:kasan_get_tag`, `kasan.h:kasan_start`, `kasan.h:kasan_stop`, `kasan.h:kasan_bypass`
- `kmap.h:kmm_map_initialize`, `kmap.h:kmm_map`, `kmap.h:kmm_unmap`, `kmap.h:kmm_map_user`, `kmap.h:kmm_map_user_page`
- `map.h:struct mm_map_entry_s`, `map.h:struct mm_map_s`, `map.h:mm_map_lock`, `map.h:mm_map_unlock`, `map.h:mm_map_initialize`, `map.h:mm_map_destroy`, `map.h:vm_alloc_region`, `map.h:vm_release_region`, `map.h:vm_map_region`, `map.h:vm_unmap_region`, `map.h:mm_map_add`, `map.h:mm_map_find`, `map.h:mm_map_remove`
- `mempool.h:struct mempool_s`, `mempool.h:struct mempool_multiple_s`, `mempool.h:struct mempoolinfo_s`, `mempool.h:mempool_init`, `mempool.h:mempool_allocate`, `mempool.h:mempool_release`, `mempool.h:mempool_info`, `mempool.h:mempool_deinit`, `mempool.h:mempool_multiple_init`, `mempool.h:mempool_multiple_alloc`, `mempool.h:mempool_multiple_free`, `mempool.h:mempool_multiple_deinit`

## Invariants
- `iob.h:CONFIG_IOB_NBUFFERS` must be strictly greater than `iob.h:CONFIG_IOB_THROTTLE` and at least `1` when `iob.h:CONFIG_MM_IOB` is enabled.
- `mm.h:MM_ALIGN` defaults to `sizeof(uintptr_t)` when `CONFIG_MM_DEFAULT_ALIGNMENT` is `0`, and `mempool.h:MEMPOOL_REALBLOCKSIZE` aligns block sizes up to `MM_ALIGN`.
- Access to `map.h:struct mm_map_s` entries must be serialized via `map.h:mm_map_lock` / `map.h:mm_map_unlock` (`mm_map_mutex`).

## Side Effects
- Heap, granule, mempool, and IOB functions mutate global and per-pool free lists, acquire spinlocks/semaphores/mutexes (`mempool.h:struct mempool_s`, `map.h:struct mm_map_s`), and may block calling threads when waiting for memory (`iob.h:iob_alloc`, `mempool.h:mempool_allocate`).
- `kmap.h:kmm_map` and `map.h:vm_map_region` modify MMU page tables and virtual address space mappings.
- `kasan.h:kasan_poison` and `kasan.h:kasan_unpoison` update KASAN shadow memory tags.

## Verification
- Run: `make test`
