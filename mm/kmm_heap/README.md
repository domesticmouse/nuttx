# kmm_heap

## Overview
Protected kernel-mode heap allocator frontend (`CONFIG_MM_KERNEL_HEAP`). Owns the global kernel heap instance `g_kmmheap` (named `"Kmem"`) and provides `kmm_*` wrapper functions that delegate to the underlying `mm_*` heap manager (`mm_heap` or `tlsf`).

## Interface
- `[kmm_initialize.c:g_kmmheap]`, `[kmm_initialize.c:kmm_initialize]`
- `[kmm_addregion.c:kmm_addregion]`, `[kmm_extend.c:kmm_extend]`, `[kmm_brkaddr.c:kmm_brkaddr]`
- `[kmm_malloc.c:kmm_malloc]`, `[kmm_free.c:kmm_free]`, `[kmm_realloc.c:kmm_realloc]`, `[kmm_memalign.c:kmm_memalign]`, `[kmm_calloc.c:kmm_calloc]`, `[kmm_zalloc.c:kmm_zalloc]`
- `[kmm_malloc_size.c:kmm_malloc_size]`, `[kmm_heapmember.c:kmm_heapmember]`
- `[kmm_mallinfo.c:kmm_mallinfo]`, `[kmm_mallinfo.c:kmm_mallinfo_task]`, `[kmm_checkcorruption.c:kmm_checkcorruption]`, `[kmm_memdump.c:kmm_memdump]`

## Invariants
- Active only when `CONFIG_MM_KERNEL_HEAP` is enabled.
- `[kmm_initialize.c:kmm_initialize]` must be called before any other `kmm_*` operation to initialize `[kmm_initialize.c:g_kmmheap]`.
- Any non-NULL pointer passed to `[kmm_free.c:kmm_free]` must belong to the kernel heap (`[kmm_heapmember.c:kmm_heapmember]`).

## Side Effects
- Initializes and mutates the global kernel heap state `[kmm_initialize.c:g_kmmheap]` via the underlying `mm_*` allocator functions.

## Verification
- Run: `make test`
