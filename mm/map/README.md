# map

## Overview
Per-process virtual memory mapping registry (`struct mm_map_s`) and virtual address region manager. Tracks active memory mappings (`mmap`, shared memory) in a task group's singly linked queue (`mm_map_sq`) and manages user-space virtual page address ranges using a granule allocator (`mm_map_vpages`) paired with MMU attachment hooks.

## Interface
- `[mm_map.c:mm_map_lock]`, `[mm_map.c:mm_map_unlock]`
- `[mm_map.c:mm_map_initialize]`, `[mm_map.c:mm_map_destroy]`
- `[mm_map.c:mm_map_add]`, `[mm_map.c:mm_map_next]`, `[mm_map.c:mm_map_find]`, `[mm_map.c:mm_map_remove]`
- `[vm_region.c:vm_alloc_region]`, `[vm_region.c:vm_release_region]`, `[vm_region.c:vm_map_region]`, `[vm_region.c:vm_unmap_region]`

## Invariants
- Total active mappings in a `struct mm_map_s` cannot exceed `CONFIG_MM_MAP_COUNT_MAX` (`[mm_map.c:mm_map_add]`).
- When `[mm_map.c:mm_map_destroy]` completes, all mapping entries have been unmapped (passing `group = NULL` to `entry->munmap` during process teardown) and `mm->map_count == 0`.
- `[vm_region.c:vm_map_region]` and `[vm_region.c:vm_unmap_region]` require non-NULL physical/virtual addresses and non-zero sizes, aligning addresses down to `MM_PGSIZE` boundaries before invoking MMU mapping operations.

## Side Effects
- Acquires recursive mutex `mm->mm_map_mutex` (`nxrmutex_lock`) when reading or mutating the mapping list (`[mm_map.c:mm_map_lock]`, `[mm_map.c:mm_map_add]`, `[mm_map.c:mm_map_remove]`).
- Allocates and frees `struct mm_map_entry_s` nodes on the kernel heap via `kmm_malloc` / `kmm_free` (`[mm_map.c:mm_map_add]`, `[mm_map.c:mm_map_remove]`).
- Allocates virtual page ranges from `mm->mm_map_vpages` via `gran_alloc` / `gran_reserve` and modifies hardware MMU page tables via `up_shmat` and `up_shmdt` (`[vm_region.c:vm_alloc_region]`, `[vm_region.c:vm_map_region]`, `[vm_region.c:vm_unmap_region]`).

## Verification
- Run: `make test`
