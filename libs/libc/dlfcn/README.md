# Dynamic Linking Interface (`libs/libc/dlfcn`)

## Overview
Implements the POSIX `<dlfcn.h>` dynamic linking loader API (`dlopen`, `dlsym`, `dlclose`, `dlerror`, `dladdr`, `dl_iterate_phdr`, `_dl_find_object`) and NuttX base symbol table registration (`dlsymtab`) on top of the `libelf` dynamic module subsystem.

## Interface
- `[lib_dlopen.c:dlopen]` - Loads an ELF shared object file into memory, resolves relocations, and returns an opaque module handle.
- `[lib_dlsym.c:dlsym]` - Resolves the runtime address of a named symbol from an open module handle.
- `[lib_dlclose.c:dlclose]` - Decrements module dependency/usage state and unloads the shared object from memory.
- `[lib_dlerror.c:dlerror]` - Returns a human-readable string describing the most recent dynamic linking error (currently stubbed to return `NULL`).
- `[lib_dladdr.c:dladdr]` - Translates a runtime symbol or code address `addr` into its containing module and nearest symbol metadata (`Dl_info`).
- `[lib_dlfind_object.c:_dl_find_object]` - Populates `struct dl_find_object` with unwinding (`PT_ARM_EXIDX` / `.eh_frame`) segment boundaries for `address`.
- `[lib_dlfind_object.c:dl_iterate_phdr]` - Iterates over loaded shared objects and invokes `callback` with each module's `struct dl_phdr_info`.
- `[lib_dlsymtab.c:dlsymtab]` - Registers the base system symbol table (`symtab`, `nsymbols`) with the dynamic loader.

## Invariants
- The base symbol table must be registered via `[lib_dlsymtab.c:dlsymtab]` (`libelf_setsymtab`) before loading modules that reference base firmware symbols (`[lib_dlopen.c:dlopen]`).
- `handle` and `name` passed to `[lib_dlsym.c:dlsym]` and `handle` passed to `[lib_dlclose.c:dlclose]` are validated with `DEBUGASSERT`.

## Side Effects
- `[lib_dlopen.c:dlopen]`, `[lib_dlclose.c:dlclose]`, and `[lib_dlfind_object.c:_dl_find_object]` acquire and release the module registry lock (`libelf_registry_lock()` / `libelf_registry_unlock()`).
- `[lib_dlopen.c:dlopen]` traverses `LD_LIBRARY_PATH` via `envpath_init()`, `envpath_next()`, and `envpath_release()` when `CONFIG_LIBC_ENVPATH` is enabled, and inserts loaded ELF objects into the module registry via `libelf_insert()`.
- `[lib_dladdr.c:dladdr]` sets thread `errno` via `set_errno()` on failure.

## Verification
- Run: `make test`
