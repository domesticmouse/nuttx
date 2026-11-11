# module

## Overview
Manages dynamically loadable kernel ELF modules (`CONFIG_MODULE`), providing module insertion (`insmod`), removal (`rmmod`), symbol resolution (`modsym`), registry locking, and `/proc/modules` status reporting (`CONFIG_FS_PROCFS`).

## Interface
- `module.h:mod_registry_lock` (`mod_registry.c:mod_registry_lock`) - Acquires the recursive mutex protecting the global module registry (`libelf_registry_lock`).
- `module.h:mod_registry_unlock` (`mod_registry.c:mod_registry_unlock`) - Releases the recursive mutex protecting the global module registry (`libelf_registry_unlock`).
- `mod_insmod.c:insmod` - Loads an ELF module from `filename` into kernel memory, registers it under `modname`, and runs its initializer.
- `mod_rmmod.c:rmmod` - Uninitializes, unloads, and unregisters a previously loaded module handle.
- `mod_modhandle.c:modhandle` - Looks up and returns the module handle (`struct module_s *`) registered under `name`.
- `mod_modsym.c:modsym` - Resolves an exported symbol name within a loaded module handle to its runtime address.
- `mod_procfs.c:g_module_operations` (`CONFIG_FS_PROCFS`) - `struct procfs_operations` table implementing `/proc/modules` open, read, dup, and close operations.

## Invariants
- All reads and modifications of `mod_registry.c:g_mod_registry` must be serialized by `mod_registry.c:mod_registry_lock`, which loops on `-EINTR` until `mod_registry.c:g_mod_lock` is acquired.
- `mod_insmod.c:insmod` rejects duplicate module names (`libelf_registry_find(modname) != NULL`) with `EEXIST`.

## Side Effects
- Loads and unloads ELF sections in kernel memory via `libelf_insert` and `libelf_remove` in `mod_insmod.c:insmod` and `mod_rmmod.c:rmmod`.
- Sets thread-local `errno` (`set_errno`) on module lookup, symbol resolution, insertion, or removal errors.
- Allocates and frees `/proc/modules` file state via `kmm_zalloc` and `kmm_free` in `mod_procfs.c:modproc_open`, `mod_procfs.c:modproc_dup`, and `mod_procfs.c:modproc_close`.

## Verification
- Run: `make test`
