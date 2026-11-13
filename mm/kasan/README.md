# kasan

## Overview
Kernel AddressSanitizer (KASan) runtime and memory error detector (`CONFIG_MM_KASAN`). Implements compiler instrumentation hooks (`__asan_load*`, `__asan_store*`, `__asan_report_*`), softwarewatchpoints (`kasan_debugpoint`), global variable redzone checking (`global.c`), and pluggable shadow/tag backends: bit-packed shadow memory (`generic.c`), software pointer tagging (`sw_tags.c`), hardware memory tagging (`hw_tags.c`), and host AddressSanitizer integration (`sim_asan.c`, `CONFIG_MM_KASAN_SIM`).

## Interface
- `[hook.c:kasan_start]`, `[hook.c:kasan_stop]`, `[hook.c:kasan_debugpoint]`
- `[hook.c:__asan_report_load_n_noabort]`, `[hook.c:__asan_report_store_n_noabort]`, `[hook.c:__asan_loadN_noabort]`, `[hook.c:__asan_storeN_noabort]`, `[hook.c:__asan_loadN]`, `[hook.c:__asan_storeN]`
- `[generic.c:kasan_register]`, `[generic.c:kasan_unregister]`, `[generic.c:kasan_poison]`, `[generic.c:kasan_unpoison]`, `[generic.c:kasan_bypass]`, `[generic.c:kasan_get_tag]`, `[generic.c:kasan_set_tag]`, `[generic.c:kasan_clear_tag]`
- `[sw_tags.c:kasan_register]`, `[sw_tags.c:kasan_unregister]`, `[sw_tags.c:kasan_poison]`, `[sw_tags.c:kasan_unpoison]`, `[sw_tags.c:kasan_bypass]`, `[sw_tags.c:kasan_get_tag]`, `[sw_tags.c:kasan_set_tag]`, `[sw_tags.c:kasan_clear_tag]`
- `[hw_tags.c:kasan_register]`, `[hw_tags.c:kasan_unregister]`, `[hw_tags.c:kasan_poison]`, `[hw_tags.c:kasan_unpoison]`, `[hw_tags.c:kasan_bypass]`, `[hw_tags.c:kasan_get_tag]`, `[hw_tags.c:kasan_set_tag]`, `[hw_tags.c:kasan_clear_tag]`
- `[sim_asan.c:kasan_register]`, `[sim_asan.c:kasan_unregister]`, `[sim_asan.c:kasan_poison]`, `[sim_asan.c:kasan_unpoison]`, `[sim_asan.c:kasan_bypass]`, `[sim_asan.c:kasan_get_tag]`, `[sim_asan.c:kasan_set_tag]`, `[sim_asan.c:kasan_clear_tag]`
- `[global.c:g_global_region]`

## Invariants
- Number of registered heap shadow regions (`g_region_count`) must not exceed `CONFIG_MM_KASAN_REGIONS` (`[generic.c:kasan_register]`, `[sw_tags.c:kasan_register]`).
- In `generic.c` and `sw_tags.c`, `[generic.c:kasan_register]` carves `KASAN_REGION_SIZE(*size)` bytes from the end of the registered memory block and decrements `*size` in place before the caller uses the region.
- Access checks in `[hook.c:kasan_check_report]` are inactive until `g_region_init == KASAN_INIT_VALUE` (`0xcafe`), which is set by `[hook.c:kasan_start]` and cleared by `[hook.c:kasan_stop]`.

## Side Effects
- Updates shadow bitmaps/tag arrays under `spin_lock_irqsave(&g_lock)` (`[generic.c:kasan_set_poison]`, `[sw_tags.c:kasan_set_poison]`) or applies hardware MTE tags via `up_memtag_set_tag` / `up_memtag_tag_mem` (`[hw_tags.c:kasan_poison_tag]`).
- Logs shadow memory hex dumps via `_alert` and triggers `PANIC()` (or `dump_stack()` when panic is disabled) upon detecting out-of-bounds, use-after-free, null-pointer, or watchpoint violations (`[hook.c:kasan_report]`).

## Verification
- Run: `make test`
