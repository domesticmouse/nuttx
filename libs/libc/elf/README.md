# ELF Module Loader and Symbol Resolver (`libs/libc/elf`)

## Overview
Implements the `libelf` runtime loader used by `dlfcn` and dynamic shared objects in NuttX (`CONFIG_LIBC_ELF`). Handles ELF header verification, section loading, XIP (`FIOC_XIPBASE` / `XIPFSIOC_PIN`) and heap/address-environment memory allocation, dynamic symbol resolution, architecture-specific relocations, `.init_array`/`.fini_array` lifecycle execution, and per-task or kernel module registry management.

## Interface
- `[elf_init.c:libelf_initialize]` - Opens an ELF file, reads its `Elf_Ehdr`, verifies the header, and initializes `struct elf_loadinfo_s`.
- `[elf_uninit.c:libelf_uninitialize]`, `[elf_uninit.c:libelf_freebuffers]` - Closes the ELF file descriptor and frees temporary loader buffers (`shdr`, `iobuffer`, `symtab`).
- `[elf_verify.c:libelf_verifyheader]` - Validates ELF magic bytes, relocatable/shared type (`ET_REL`, `ET_DYN`), and target architecture via `up_checkarch()`.
- `[elf_load.c:libelf_load]`, `[elf_load.c:libelf_load_with_addrenv]`, `[elf_load.c:libelf_pinrelease]` - Allocates memory or pins XIP pages, loads ELF sections, and extracts unwinding (`exidx` / `eh_frame`) metadata.
- `[elf_unload.c:libelf_unload]` - Unloads ELF text/data allocations and releases the module's address environment.
- `[elf_bind.c:libelf_bind]` - Processes `SHT_REL` and `SHT_RELA` relocation sections, resolves imported symbols, and synchronizes instruction/data caches.
- `[elf_insert.c:libelf_insert]` - Loads, binds, registers a new ELF module `struct module_s`, and runs its `.preinit_array` and `.init_array` initializers.
- `[elf_remove.c:libelf_remove]`, `[elf_remove.c:libelf_removeall]`, `[elf_remove.c:libelf_uninit]` - Executes `.fini_array` destructors, removes modules from the registry, and frees module memory.
- `[elf_depend.c:libelf_depend]`, `[elf_depend.c:libelf_undepend]` - Tracks and releases directed dependency edges (`struct mod_depend_s`) between exporter and importer modules (`CONFIG_MODLIB_HAVE_SYMTAB`).
- `[elf_registry.c:libelf_registry_add]`, `[elf_registry.c:libelf_registry_del]`, `[elf_registry.c:libelf_registry_find]`, `[elf_registry.c:libelf_registry_verify]`, `[elf_registry.c:libelf_registry_foreach]` - Manages the linked list of loaded `struct module_s` instances.
- `[elf_symbols.c:libelf_symname]`, `[elf_symbols.c:libelf_findsymtab]`, `[elf_symbols.c:libelf_readsym]`, `[elf_symbols.c:libelf_symvalue]`, `[elf_symbols.c:libelf_insertsymtab]`, `[elf_symbols.c:libelf_findglobal]`, `[elf_symbols.c:libelf_freesymtab]`, `[elf_symbols.c:libelf_findsymbol]` - Parses ELF symbol tables, exports dynamic symbols, and resolves symbol addresses across loaded modules.
- `[elf_symtab.c:libelf_getsymtab]`, `[elf_symtab.c:libelf_setsymtab]` - Gets and sets the global base firmware symbol table Descriptor.
- `[elf_gethandle.c:libelf_gethandle]`, `[elf_getsymbol.c:libelf_getsymbol]` - High-level module handle lookup by name and symbol value lookup by handle.
- `[elf_addrenv.c:libelf_addrenv_alloc]`, `[elf_addrenv.c:libelf_addrenv_select]`, `[elf_addrenv.c:libelf_addrenv_restore]`, `[elf_addrenv.c:libelf_addrenv_free]` - Manages `CONFIG_ARCH_ADDRENV` virtual address environments for loaded ELF modules.
- `[elf_loadhdrs.c:libelf_loadhdrs]`, `[elf_read.c:libelf_read]`, `[elf_sections.c:libelf_sectname]`, `[elf_sections.c:libelf_findsection]`, `[elf_iobuffer.c:libelf_allocbuffer]`, `[elf_iobuffer.c:libelf_reallocbuffer]` - Internal header, section, file read, and I/O buffer helpers.

## Invariants
- Callers of `[elf_insert.c:libelf_insert]`, `[elf_remove.c:libelf_remove]`, `[elf_depend.c:libelf_depend]`, `[elf_depend.c:libelf_undepend]`, and `[elf_registry.c:libelf_registry_add]` must hold the module registry lock (`libelf_registry_lock()`).
- `[elf_remove.c:libelf_remove]` refuses to unload a module with `modp->dependents > 0`, returning `-EBUSY`.
- Section alignments processed by `[elf_load.c:libelf_load]` must be powers of two (`(shdr->sh_addralign & (shdr->sh_addralign - 1)) == 0`).

## Side Effects
- Opens and reads ELF files via `_NX_OPEN`, `_NX_SEEK`, `_NX_READ`, `_NX_CLOSE`, and queries XIP mappings via `_NX_IOCTL` (`XIPFSIOC_PIN`, `FIOC_XIPBASE`) (`[elf_init.c:libelf_initialize]`, `[elf_load.c:libelf_load]`).
- Allocates and frees module metadata, symbol tables, and text/data memory from heap or `up_addrenv_create()` (`[elf_load.c:libelf_load]`, `[elf_addrenv.c:libelf_addrenv_alloc]`).
- Modifies loaded code/data sections during relocation, flushes CPU data/instruction caches via `up_coherent_dcache()`, and invokes loaded module `.preinit_array`, `.init_array`, and `.fini_array` function pointers (`[elf_bind.c:libelf_bind]`, `[elf_insert.c:libelf_insert]`, `[elf_remove.c:libelf_uninit]`).
- Acquires and releases `g_libelf_symlock` when reading or updating the global symbol table (`[elf_symtab.c:libelf_getsymtab]`, `[elf_symtab.c:libelf_setsymtab]`).

## Verification
- Run: `make test`
