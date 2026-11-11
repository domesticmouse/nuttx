# x86_64 Machine Support (`libs/libc/machine/x86_64`)

## Overview
Provides x86_64 cache-size constants for assembly string/memory routines and 64-bit AMD64 ELF header validation and relocation support.

## Interface
- `cache.h:SHARED_CACHE_SIZE`, `cache.h:DATA_CACHE_SIZE`, `cache.h:SHARED_CACHE_SIZE_HALF`, `cache.h:DATA_CACHE_SIZE_HALF` - L1 data cache and L2 shared cache size constants used by SSE2/AVX2 memory routines.
- `arch_elf64.c:up_checkarch` - Validates that an `Elf64_Ehdr` header targets `EM_X86_64`, `ELFCLASS64`, and little-endian (`ELFDATA2LSB`).
- `arch_elf64.c:up_relocate` - Returns `-ENOSYS` for `Elf64_Rel` relocations.
- `arch_elf64.c:up_relocateadd` - Applies 64-bit `Elf64_Rela` relocations (`R_X86_64_NONE`, `R_X86_64_64`, `R_X86_64_PC32`, `R_X86_64_PLT32`, `R_X86_64_32`, `R_X86_64_32S`, `R_X86_64_GOTPCRELX`, `R_X86_64_REX_GOTPCRELX`).

## Invariants
- `arch_elf64.c:up_checkarch` enforces little-endian (`ELFDATA2LSB`) 64-bit `EM_X86_64` ELF objects (failing compilation if `CONFIG_ENDIAN_BIG` is set).
- `arch_elf64.c:up_relocateadd` requires `sym != NULL` for all relocations other than `R_X86_64_NONE` and verifies 32-bit truncation bounds before patching.

## Side Effects
- `arch_elf64.c:up_relocateadd` patches 32-bit/64-bit words and rewrites `MOV` (`0x8b`) to `LEA` (`0x8d`) instructions for `GOTPCRELX` relocations at `addr`, logging errors via `berr`.

## Verification
- Run: `make test`
