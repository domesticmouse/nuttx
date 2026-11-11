# File and Anonymous Memory Mapping (mmap)

## Overview
Implements POSIX `mmap`, `munmap`, `msync`, `mprotect`, and `mlock`/`munlock` interfaces for NuttX, supporting direct XIP/driver memory mappings, anonymous page/heap mappings (`MAP_ANONYMOUS`), and simulated RAM-copied file mappings (`CONFIG_FS_RAMMAP`) on flat-address-space targets.

## Interface
- `fs_mmap.c:mmap`, `fs_mmap.c:file_mmap` - User and kernel-internal memory mapping entry points.
- `fs_munmap.c:munmap`, `fs_munmap.c:file_munmap` - User and kernel-internal unmapping functions.
- `fs_msync.c:msync` - Synchronizes shared memory-mapped regions back to their backing store.
- `fs_rammap.h:rammap`, `fs_rammap.h:enum mm_map_type_e` - Fallback RAM-copy file mapping implementation (`MAP_USER`, `MAP_KERNEL`, `MAP_XIP`).
- `fs_anonmap.c:map_anonymous` - Allocates zero-initialized or uninitialized anonymous memory mappings from heap or kernel page pools.
- `fs_mmisc.c:mprotect`, `fs_mmisc.c:mlock`, `fs_mmisc.c:mlockall`, `fs_mmisc.c:munlock`, `fs_mmisc.c:munlockall` - Memory protection and page locking APIs.

## Invariants
- Callers to `fs_mmap.c:mmap` must specify either `MAP_PRIVATE` or `MAP_SHARED` (never both) and a non-zero `length`; `MAP_FIXED` and `MAP_DENYWRITE` are rejected with `-ENOSYS`.
- Modifications to the process or task-group `mm_map_s` mapping list in `fs_munmap.c:file_munmap_`, `fs_msync.c:msync`, and `fs_mmisc.c:mprotect` must hold `mm_map_lock()`.
- Partial unmapping in `fs_anonmap.c:unmap_anonymous` and `fs_rammap.c` must extend to the end of the mapped region; unmapping a middle hole returns `-ENOSYS`.

## Side Effects
- Allocates virtual/physical pages (`mm_pgalloc`, `vm_alloc_region`, `up_shmat`) or heap buffers (`fs_heap_zalloc`, `kumm_zalloc`) and registers entries in the current task group's `mm_map_s` table.
- Reads backing file contents into RAM buffers during `fs_rammap.h:rammap` and flushes data cache when `PROT_EXEC` is applied in `fs_mmisc.c:mprotect`.

## Verification
- Run: `make test`
