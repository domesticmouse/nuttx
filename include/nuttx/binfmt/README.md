# Binary Format Loader Headers (`include/nuttx/binfmt`)

## Overview
Defines the NuttX binary format (`binfmt`) loader framework, including pluggable format registration, module loading/unloading, process execution (`exec`/`exec_spawn`), symbol table binding, and format-specific loaders for ELF, NXFLAT, and IEEE-695 object files.

## Interface
- `binfmt.h:binary_s`, `binfmt.h:binfmt_s`, `binfmt.h:binfmt_ctor_t`, `binfmt.h:binfmt_dtor_t` - Loaded binary descriptor, binary format loader registration structure, and C++ constructor/destructor function pointer types.
- `binfmt.h:binfmt_initialize`, `binfmt.h:register_binfmt`, `binfmt.h:unregister_binfmt`, `binfmt.h:load_module`, `binfmt.h:unload_module`, `binfmt.h:exec_module`, `binfmt.h:exec`, `binfmt.h:exec_spawn`, `binfmt.h:binfmt_exit` - Core binary loader lifecycle, registration, symbol export binding, and task execution APIs.
- `elf.h:elf_loadinfo_s`, `elf.h:elf_init`, `elf.h:elf_uninit`, `elf.h:elf_load`, `elf.h:elf_bind`, `elf.h:elf_unload` - ELF binary parser, section allocator, relocation binder, and unloader interfaces.
- `nxflat.h:nxflat_loadinfo_s`, `nxflat.h:nxflat_init`, `nxflat.h:nxflat_uninit`, `nxflat.h:nxflat_load`, `nxflat.h:nxflat_read`, `nxflat.h:nxflat_bind`, `nxflat.h:nxflat_unload` - NXFLAT XIP binary format loader and relocation interfaces.
- `ieee695.h:ieee695_record_s`, `ieee695.h:ieee695_theadr_s`, `ieee695.h:ieee695_lheadr_s`, `ieee695.h:ieee695_coment_s`, `ieee695.h:ieee695_modend_s`, `ieee695.h:SIZEOF_IEEE695_RECORD` - IEEE-695 object format record definitions and constants.
- `symtab.h:exec_getsymtab`, `symtab.h:exec_setsymtab` - Global execution symbol table getter and setter.

## Invariants
- `binfmt.h:binfmt_s` instances registered via `register_binfmt` must provide a valid `load` callback; `binary_s` allocations are bounded by `binfmt.h:BINFMT_NALLOC`.
- When `CONFIG_ARCH_ADDRENV` is enabled, `elf_loadinfo_s`, `nxflat_loadinfo_s`, and `binary_s` maintain address environment handles (`addrenv`, `oldenv`) that must be restored or freed upon unload.

## Side Effects
- `binfmt.h:load_module`, `elf.h:elf_load`, and `nxflat.h:nxflat_load` open executable files in the VFS, allocate kernel/user memory or address environments, and perform symbol relocations.
- `binfmt.h:exec`, `binfmt.h:exec_spawn`, and `binfmt.h:exec_module` spawn new tasks/processes and execute C++ static constructors (`ctors`).
- `symtab.h:exec_setsymtab` mutates the global symbol table pointer and count used for dynamic symbol resolution.

## Verification
- Run: `make test`
