# shm

## Overview
POSIX System V shared memory (`sys/shm.h`) subsystem for NuttX kernel builds (`CONFIG_MM_SHM`). Manages a global table of shared memory regions (`g_shminfo`), backs each region with physical pages from the page allocator (`mm_pgalloc`), and maps/unmaps them into task group virtual address spaces via `vm_alloc_region` and architecture MMU hooks (`up_shmat`, `up_shmdt`).

## Interface
- `[shm.h:struct shm_region_s]`, `[shm.h:struct shm_info_s]`, `[shm.h:g_shminfo]`
- `[shmget.c:shmget]`
- `[shmat.c:shmat]`
- `[shmdt.c:shmdt]`
- `[shmctl.c:shmctl]`, `[shmctl.c:shm_destroy]`

## Invariants
- Requires `CONFIG_ARCH_ADDRENV`, `CONFIG_BUILD_KERNEL`, `CONFIG_GRAN`, and `CONFIG_MM_PGALLOC` to be enabled (`[shm.h:CONFIG_ARCH_ADDRENV]`).
- Shared memory identifiers (`shmid`) are bounded within `[0, CONFIG_ARCH_SHM_MAXREGIONS)` and must have `[shm.h:SRFLAG_INUSE]` set to be attached or controlled (`[shmat.c:shmat]`, `[shmctl.c:shmctl]`).
- A region marked with `IPC_RMID` while `shm_nattch > 0` sets `[shm.h:SRFLAG_UNLINKED]` and defers `[shmctl.c:shm_destroy]` until the last attached process detaches (`[shmat.c:munmap_shm]`, `[shmctl.c:shmctl]`).

## Side Effects
- Acquires global table mutex `[shm.h:g_shminfo]` (`si_lock`) or per-region mutex `sr_lock` (`[shmget.c:shmget]`, `[shmat.c:shmat]`, `[shmctl.c:shmctl]`).
- Allocates and frees physical pages via `mm_pgalloc` / `mm_pgfree` and page arrays via `kmm_realloc` / `kmm_free` (`[shmget.c:shm_extend]`, `[shmctl.c:shm_destroy]`).
- Modifies task group virtual memory mappings (`vm_alloc_region`, `vm_release_region`, `mm_map_add`, `mm_map_remove`) and invokes hardware MMU page table operations `up_shmat` / `up_shmdt` (`[shmat.c:shmat]`, `[shmat.c:munmap_shm]`).

## Verification
- Run: `make test`
