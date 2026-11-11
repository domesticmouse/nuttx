# Kernel Dynamic Virtual Memory Mapping (`mm/kmap`)

## Overview
Implements dynamic kernel virtual memory mapping (`kmm_map`) for `CONFIG_BUILD_KERNEL` configurations. Allows kernel code to map arbitrary arrays of physical page frames or user-space virtual memory ranges into a contiguous kernel virtual address region (`[CONFIG_ARCH_KMAP_VBASE, ARCH_KMAP_VEND]`) managed by a granule allocator (`g_kmm_map_vpages`) and a mapping tracking list (`g_kmm_map`).

## Interface
- `[kmm_map.c:kmm_map_initialize]` - Initializes the kernel virtual page granule allocator (`g_kmm_map_vpages`), the mapping list (`g_kmm_map`), and the architecture-specific kernel mapping page tables (`up_addrenv_kmap_init`)
- `[kmm_map.c:kmm_map]` - Maps an array of `npages` physical page addresses (`pages`) into contiguous kernel virtual memory and returns the mapped base address
- `[kmm_map.c:kmm_unmap]` - Unmaps a previously mapped kernel virtual address region (`kaddr`), tearing down MMU mappings and releasing virtual pages if dynamically allocated
- `[kmm_map.c:kmm_map_user]` - Resolves a user-space buffer `[uaddr, uaddr + size)` from the active task group's address environment into physical pages and maps them contiguously into kernel virtual space
- `[kmm_map.c:kmm_map_user_page]` - Resolves and maps a single user-space page containing `uaddr` directly into its kernel virtual address equivalent

## Invariants
- Active only when `CONFIG_BUILD_KERNEL` is enabled.
- `[kmm_map.c:kmm_map]` requires `pages != NULL` and `0 < npages <= CONFIG_ARCH_KMAP_NPAGES`.
- Single-page mappings (`npages == 1`) do not consume dynamic virtual space from `g_kmm_map_vpages`; they resolve directly via `up_addrenv_page_vaddr`.
- Multi-page mappings (`npages > 1`) reside within `[CONFIG_ARCH_KMAP_VBASE, ARCH_KMAP_VEND)` (`[kmm_map.c:is_kmap_vaddr]`) and record a `struct mm_map_entry_s` in `g_kmm_map`.

## Side Effects
- Initializes and mutates module-global state `g_kmm_map_vpages` and `g_kmm_map` (`[kmm_map.c:kmm_map_initialize]`, `[kmm_map.c:kmm_map]`, `[kmm_map.c:kmm_unmap]`).
- Acquires and releases the recursive mapping mutex `g_kmm_map.mm_map_mutex` via `[kmm_map.c:kmm_map_lock]` and `[kmm_map.c:kmm_map_unlock]`.
- Allocates and frees temporary physical page pointer arrays on the kernel heap via `kmm_zalloc` and `kmm_free` (`[kmm_map.c:kmm_map_user]`).
- Modifies hardware MMU kernel page tables via `up_addrenv_kmap_init`, `up_addrenv_kmap_pages`, and `up_addrenv_kunmap_pages`.

## Verification
- Run: `make test`
