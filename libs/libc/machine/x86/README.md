# x86 (i386/i486) Machine Support (`libs/libc/machine/x86`)

## Overview
Provides 32-bit x86 (`EM_386`/`EM_486`) ELF header validation and relocation routines for the NuttX ELF binary loader.

## Interface
- `arch_elf.c:up_checkarch` - Verifies that an `Elf32_Ehdr` header targets `EM_386` or `EM_486`.
- `arch_elf.c:up_relocate` - Applies `Elf32_Rel` relocations (`R_386_32`, `R_386_PC32`) at `addr`.
- `arch_elf.c:up_relocateadd` - Logs a warning and returns `-ENOSYS` for `Elf32_Rela` relocations.

## Invariants
- `arch_elf.c:up_relocate` requires `sym != NULL` and returns `-EINVAL` for null symbols or unrecognized relocation types.

## Side Effects
- `arch_elf.c:up_relocate` mutates the 32-bit word at `addr` in place; `arch_elf.c:up_relocateadd` logs warnings via `bwarn`.

## Verification
- Run: `make test`
