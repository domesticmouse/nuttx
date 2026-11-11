# mempool

## Overview
Fixed-block and multi-bucket memory pool allocator subsystem (`CONFIG_MM_PGALLOC` / `CONFIG_MM_HEAP_MEMPOOL`). Provides single-size block pools (`struct mempool_s`) with dedicated interrupt queues (`iqueue`), dynamic chunk expansion (`equeue`), optional blocking wait semaphores, and multi-pool aggregators (`struct mempool_multiple_s`) indexed by a 2D expansion dictionary (`mpool_dict_s`), plus a procfs status interface (`g_mempool_operations`).

## Interface
- `[mempool.c:mempool_init]`, `[mempool.c:mempool_allocate]`, `[mempool.c:mempool_release]`, `[mempool.c:mempool_deinit]`
- `[mempool.c:mempool_info]`, `[mempool.c:mempool_info_task]`, `[mempool.c:mempool_memdump]`
- `[mempool_multiple.c:struct mempool_multiple_s]`, `[mempool_multiple.c:mempool_multiple_init]`, `[mempool_multiple.c:mempool_multiple_deinit]`
- `[mempool_multiple.c:mempool_multiple_alloc]`, `[mempool_multiple.c:mempool_multiple_realloc]`, `[mempool_multiple.c:mempool_multiple_free]`, `[mempool_multiple.c:mempool_multiple_memalign]`, `[mempool_multiple.c:mempool_multiple_alloc_size]`
- `[mempool_multiple.c:mempool_multiple_foreach]`, `[mempool_multiple.c:mempool_multiple_mallinfo]`, `[mempool_multiple.c:mempool_multiple_info_task]`, `[mempool_multiple.c:mempool_multiple_memdump]`
- `[mempool_procfs.c:g_mempool_operations]`, `[mempool_procfs.c:mempool_procfs_register]`, `[mempool_procfs.c:mempool_procfs_unregister]`

## Invariants
- `[mempool_multiple.c:mempool_multiple_init]` requires `expandsize` to be a power of two (`(expandsize & (expandsize - 1)) == 0`) so that allocated blocks can be mapped back to their expansion dictionary entry via `ALIGN_DOWN(blk, mpool->expandsize)` (`[mempool_multiple.c:mempool_multiple_get_dict]`).
- `[mempool.c:mempool_deinit]` fails with `-EBUSY` if `pool->nalloc != 0` (all allocated blocks must be released prior to pool teardown).
- When `CONFIG_MM_BACKTRACE >= 0`, every block carries a trailing `struct mempool_backtrace_s` whose `magic` field transitions strictly between `[mempool.c:MEMPOOL_MAGIC_FREE]` (`0x55555555`) and `[mempool.c:MEMPOOL_MAGIC_ALLOC]` (`0xAAAAAAAA`) to detect double-frees and buffer overruns (`[mempool.c:mempool_release]`).

## Side Effects
- Synchronizes per-pool block queues (`queue`, `iqueue`, `equeue`) with `spin_lock_irqsave(&pool->lock)` and multi-pool chunk/dictionary state with recursive mutex `nxrmutex_lock(&mpool->lock)` (`[mempool.c:mempool_allocate]`, `[mempool_multiple.c:mempool_multiple_alloc_callback]`).
- Invokes user-supplied `alloc` and `free` callbacks to acquire/release backing memory chunks and poisons/unpoisons blocks via KASan (`[mempool.c:mempool_init]`, `[mempool.c:mempool_allocate]`, `[mempool.c:mempool_release]`).
- Registers/unregisters procfs entries on `g_mempool_procfs` (`[mempool_procfs.c:mempool_procfs_register]`) and blocks/wakes threads via `pool->waitsem` when `pool->wait && pool->expandsize == 0`.

## Verification
- Run: `make test`
