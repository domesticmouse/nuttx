# I/O Buffer Subsystem (`mm/iob`)

## Overview
Provides a deterministic, fixed-size and dynamically extensible I/O Buffer (`struct iob_s`) management subsystem (`CONFIG_MM_IOB`) used primarily by network stacks, wireless drivers, and streaming device drivers. Supports chaining multiple small buffers into larger packet frames (`io_flink`), queueing packet chains via queue entries (`struct iob_qentry_s`), producer throttling (`CONFIG_IOB_THROTTLE`), scatter/gather `iovec` copying, headroom reservation, contiguity packing, and asynchronous availability notifications.

## Interface
- `[iob.h:g_iob_freelist]`, `[iob.h:g_iob_committed]`, `[iob.h:g_iob_sem]`, `[iob.h:g_iob_count]`, `[iob.h:g_iob_lock]` - Internal global free list, committed list, counting semaphore, availability counter, and spinlock
- `[iob_initialize.c:iob_initialize]` - Initializes pre-allocated IOB pools (`g_iob_buffer`), queue entry pools (`g_iob_qpool`), counting semaphores, and spinlocks
- `[iob_alloc.c:iob_alloc]`, `[iob_alloc.c:iob_timedalloc]`, `[iob_alloc.c:iob_tryalloc]` - Blocking, timeout-bounded, and non-blocking IOB allocation with optional producer throttling
- `[iob_alloc.c:iob_alloc_dynamic]`, `[iob_alloc.c:iob_alloc_with_data]`, `[iob_alloc.c:iob_init_with_data]` - Dynamic heap-backed and external-buffer-backed IOB allocation (`CONFIG_IOB_ALLOC`)
- `[iob_free.c:iob_free]` - Frees a single IOB in a chain, returns the next buffer in the chain, updates `io_pktlen`, and wakes waiting threads or work-queue notifiers
- `[iob_free_chain.c:iob_free_chain]` - Frees an entire linked chain of IOBs
- `[iob_alloc_qentry.c:iob_alloc_qentry]`, `[iob_alloc_qentry.c:iob_tryalloc_qentry]`, `[iob_free_qentry.c:iob_free_qentry]` - Allocates and frees IOB queue container nodes (`struct iob_qentry_s`)
- `[iob_add_queue.c:iob_add_queue]`, `[iob_add_queue.c:iob_tryadd_queue]`, `[iob_add_queue.c:iob_concat_queue]` - Appends or concatenates IOB chains onto an `iob_queue_s`
- `[iob_remove_queue.c:iob_remove_queue]`, `[iob_peek_queue.c:iob_peek_queue]` - Dequeues or inspects the head IOB chain from an `iob_queue_s`
- `[iob_free_queue.c:iob_free_queue]`, `[iob_free_queue_qentry.c:iob_free_queue_qentry]` - Frees all IOB chains and queue entries held in an `iob_queue_s`
- `[iob_get_queue_info.c:iob_get_queue_size]`, `[iob_get_queue_info.c:iob_get_queue_entry_count]` - Returns total byte count or entry count queued in an `iob_queue_s`
- `[iob_copyin.c:iob_copyin]`, `[iob_copyin.c:iob_trycopyin]`, `[iob_copyin.c:iob_copyin_iov]`, `[iob_copyin.c:iob_trycopyin_iov]` - Copies linear buffers or `struct iovec` arrays into an IOB chain at a specified offset, extending the chain as needed
- `[iob_copyout.c:iob_copyout]`, `[iob_copyout.c:iob_copyout_iov]` - Copies data out of an IOB chain into a linear buffer or `struct iovec` array without consuming the chain
- `[iob_clone.c:iob_clone]`, `[iob_clone.c:iob_clone_partial]` - Deep-copies a full or partial IOB chain into a newly allocated IOB chain
- `[iob_concat.c:iob_concat]` - Concatenates two IOB chains and updates the head `io_pktlen`
- `[iob_contig.c:iob_contig]`, `[iob_pack.c:iob_pack]` - Packs data across an IOB chain to ensure the leading `len` bytes are contiguous or to eliminate unused space
- `[iob_trimhead.c:iob_trimhead]`, `[iob_trimhead_queue.c:iob_trimhead_queue]`, `[iob_trimtail.c:iob_trimtail]` - Trims bytes from the beginning or end of an IOB chain, releasing emptied nodes
- `[iob_reserve.c:iob_reserve]` - Adjusts headroom offset (`io_offset`) at the front of an IOB chain
- `[iob_update_pktlen.c:iob_update_pktlen]` - Recomputes and updates `io_pktlen` on the head node of a chain and trims excess buffers
- `[iob_tailroom.c:iob_tailroom]`, `[iob_count.c:iob_count]`, `[iob_navail.c:iob_navail]`, `[iob_statistics.c:iob_getstats]` - Queries remaining tailroom, chain node count, free IOB availability, and global statistics (`struct iob_stats_s`)
- `[iob_notifier.c:iob_notifier_setup]`, `[iob_notifier.c:iob_notifier_teardown]`, `[iob_notifier.c:iob_notifier_signal]` - Registers and triggers work-queue notifications when free IOBs become available (`CONFIG_IOB_NOTIFIER`)
- `[iob_dump.c:iob_dump]` - Formats and logs hexadecimal diagnostics of an IOB chain (`CONFIG_DEBUG_FEATURES`)

## Invariants
- Every static buffer in `g_iob_buffer` has its `io_data` payload aligned to `IOB_ALIGNMENT` (`[iob_initialize.c:iob_initialize]`).
- `io_pktlen` is valid only on the head node of an IOB chain and must equal the sum of `io_len` across all nodes in the chain; freeing the head node transfers `io_pktlen - io_len` to the successor node (`[iob_free.c:iob_free]`).
- Throttled allocation (`throttled == true`) succeeds only when available buffers exceed `CONFIG_IOB_THROTTLE` (`[iob_alloc.c:iob_tryalloc_internal]`).
- `[iob_contig.c:iob_contig]` requires `len <= IOB_BUFSIZE(iob)`.

## Side Effects
- Acquires and releases interrupt-saving spinlocks (`spin_lock_irqsave(&g_iob_lock)`) when mutating global pools (`g_iob_freelist`, `g_iob_committed`, `g_iob_freeqlist`, `g_iob_qcommitted`) and counters (`g_iob_count`, `g_throttle_wait`, `g_qentry_wait`).
- Blocks and wakes threads on counting semaphores `g_iob_sem`, `g_throttle_sem`, and `g_qentry_sem` (`[iob_alloc.c:iob_alloc_wait]`, `[iob_free.c:iob_free]`).
- Signals work-queue notification handlers via `work_notifier_signal` when buffers are freed (`[iob_notifier.c:iob_notifier_signal]`).
- Allocates and frees dynamic memory on the kernel heap via `kmm_memalign`, `kmm_zalloc`, `kmm_free`, or custom `io_free` callbacks when `CONFIG_IOB_ALLOC` is enabled (`[iob_alloc.c:iob_alloc_dynamic]`, `[iob_free.c:iob_free]`).

## Verification
- Run: `make test`
