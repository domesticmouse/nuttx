# Simulator Machine Support (`libs/libc/machine/sim`)

## Overview
Provides 32-bit (`EM_386`) and 64-bit (`EM_X86_64`) ELF header verification and symbol relocation support for the NuttX host simulator architecture.

## Interface
- `arch_elf.c:up_checkarch` - Verifies that a 32-bit `Elf32_Ehdr` header targets `EM_386` or `EM_486`.
- `arch_elf.c:up_relocate` - Applies 32-bit x86 `Elf32_Rel` relocations (`R_386_32`, `R_386_PC32`) at `addr`.
- `arch_elf.c:up_relocateadd` - Returns `-ENOSYS` for 32-bit `Elf32_Rela` relocations.
- `arch_elf64.c:up_checkarch` - Verifies that a 64-bit `Elf64_Ehdr` header targets `EM_X86_64`, `ELFCLASS64`, and little-endian (`ELFDATA2LSB`).
- `arch_elf64.c:up_relocate` - Returns `-ENOSYS` for 64-bit `Elf64_Rel` relocations.
- `arch_elf64.c:up_relocateadd` - Applies 64-bit x86_64 `Elf64_Rela` relocations (`R_X86_64_NONE`, `R_X86_64_64`, `R_X86_64_PC32`, `R_X86_64_PLT32`, `R_X86_64_32`, `R_X86_64_32S`, `R_X86_64_PC64`).

## Invariants
- `arch_elf.c:up_relocate` and `arch_elf64.c:up_relocateadd` require `sym != NULL` (except for `R_X86_64_NONE`).
- `arch_elf64.c:up_relocateadd` verifies that 32-bit zero-extended (`R_X86_64_32`) and sign-extended (`R_X86_64_32S`, `R_X86_64_PC32`, `R_X86_64_PLT32`) relocated values do not truncate when cast, returning `-EINVAL` on overflow.

## Side Effects
- `arch_elf.c:up_relocate` and `arch_elf64.c:up_relocateadd` mutate target memory words at `addr` and log relocation errors via `berr`.

## Verification
- Run: `make test`
