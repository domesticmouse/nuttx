# SPARC Machine Support (`libs/libc/machine/sparc`)

## Overview
Provides 32-bit SPARC (`EM_SPARC`) ELF header verification and instruction/data relocation support for the NuttX ELF binary loader.

## Interface
- `arch_elf.c:up_checkarch` - Verifies that an `Elf32_Ehdr` header targets `EM_SPARC`, `ELFCLASS32`, and matches system endianness (`CONFIG_ENDIAN_BIG`).
- `arch_elf.c:up_relocate` - Validates arguments for `Elf32_Rel` relocations and returns `-EINVAL` for unsupported non-`R_SPARC_NONE` relocations.
- `arch_elf.c:up_relocateadd` - Applies `Elf32_Rela` SPARC relocations (`R_SPARC_NONE`, `R_SPARC_8`, `R_SPARC_16`, `R_SPARC_32`, `R_SPARC_DISP8`, `R_SPARC_DISP16`, `R_SPARC_DISP32`, `R_SPARC_WDISP30`, `R_SPARC_HI22`, `R_SPARC_LO10`, `R_SPARC_UA32`).

## Invariants
- `arch_elf.c:up_checkarch` requires `ehdr->e_machine == EM_SPARC` and `ehdr->e_ident[EI_CLASS] == ELFCLASS32`.
- `arch_elf.c:up_relocate` and `arch_elf.c:up_relocateadd` require `sym != NULL` for all relocation types except `R_SPARC_NONE`.

## Side Effects
- `arch_elf.c:up_relocateadd` patches SPARC instructions and unaligned/aligned data words in memory at `addr` and logs errors via `berr`.

## Verification
- Run: `make test`
