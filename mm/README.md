# Memory Management Subsystem (`mm`)

## Overview
Root directory for the NuttX Memory Management (`mm`) subsystem. Groups heap allocators (standard best-fit, TLSF, fixed-block mempool, and page-aligned granule allocators), user and kernel heap wrappers (`umm_heap`, `kmm_heap`), virtual memory mapping registries (`map`, `kmap`), System V shared memory (`shm`), network/driver I/O buffers (`iob`), and runtime memory/behavior sanitizers (`kasan`, `ubsan`).

## Subdirectories & Boundaries
- **Core Heap Allocator (`mm_heap`)**: [./mm_heap/README.md](./mm_heap/README.md) - Multi-instance heap allocator implementing `mm_malloc`, `mm_free`, `mm_realloc`, `mm_memalign`, and heap inspection routines.
- **User Heap Wrapper (`umm_heap`)**: [./umm_heap/README.md](./umm_heap/README.md) - Standard C library and user-space heap allocation interface (`malloc`, `free`, `realloc`, `memalign`, `sbrk`) routing to `USR_HEAP`.
- **Kernel Heap Wrapper (`kmm_heap`)**: [./kmm_heap/README.md](./kmm_heap/README.md) - Kernel-space heap allocation interface (`kmm_malloc`, `kmm_free`, `kmm_realloc`, `kmm_memalign`) routing to `g_kmmheap`.
- **TLSF Heap Allocator (`tlsf`)**: [./tlsf/README.md](./tlsf/README.md) - $O(1)$ Two-Level Segregated Fit (`mm_tlsf`) heap backend with integrated mempool and KASAN support.
- **Fixed-Block Memory Pool (`mempool`)**: [./mempool/README.md](./mempool/README.md) - Single-block-size and multi-pool (`mempool_multiple`) deterministic block allocators and procfs diagnostics.
- **Granule Allocator (`mm_gran`)**: [./mm_gran/README.md](./mm_gran/README.md) - Bitmap-based power-of-two granule and DMA/page allocator (`gran_alloc`, `gran_free`, `gran_reserve`).
- **Virtual Memory Mapping Registry (`map`)**: [./map/README.md](./map/README.md) - Per-process/task-group virtual memory mapping list (`struct mm_map_s`) and anonymous `rammap` emulation.
- **Kernel Dynamic Virtual Memory Mapping (`kmap`)**: [./kmap/README.md](./kmap/README.md) - Dynamic kernel virtual address space page mapping (`kmm_map`, `kmm_unmap`, `kmm_map_user`) for `CONFIG_BUILD_KERNEL`.
- **System V Shared Memory (`shm`)**: [./shm/README.md](./shm/README.md) - POSIX/System V shared memory interface (`shmget`, `shmat`, `shmdt`, `shmctl`) backed by page pools and task-group virtual mappings.
- **I/O Buffer Subsystem (`iob`)**: [./iob/README.md](./iob/README.md) - Chained and queued fixed/dynamic I/O buffers (`struct iob_s`) with producer throttling and notifier callbacks.
- **Kernel Address Sanitizer (`kasan`)**: [./kasan/README.md](./kasan/README.md) - Software shadow-memory and hardware tag-based (`sw_tags`, `hw_tags`, `generic`) memory access sanitizer runtime.
- **UndefinedBehaviorSanitizer Runtime (`ubsan`)**: [./ubsan/README.md](./ubsan/README.md) - Compiler-instrumented undefined behavior trap handlers (`__ubsan_handle_*`).
