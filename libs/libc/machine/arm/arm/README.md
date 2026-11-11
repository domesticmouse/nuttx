# ARM32 Classic ELF Relocation (`libs/libc/machine/arm/arm`)

## Overview
Provides architecture-specific 32-bit ELF header validation and symbol relocation routines for classic ARM (ARMv4/ARMv5) targets used by the NuttX binary loader and dynamic linker.

## Interface
- `arch_elf.c:up_checkarch` - Validates that a 32-bit ELF header (`Elf32_Ehdr`) targets `EM_ARM`, `ELFCLASS32`, the configured endianness (`CONFIG_ENDIAN_BIG`), and proper entry-point alignment (`CONFIG_ARM_THUMB`).
- `arch_elf.c:up_relocate` - Applies `Elf32_Rel` relocations (such as `R_ARM_NONE`, `R_ARM_ABS32`, `R_ARM_PC24`, `R_ARM_CALL`, `R_ARM_JUMP24`, `R_ARM_THM_CALL`, `R_ARM_V4BX`, `R_ARM_PREL31`, `R_ARM_MOVW_ABS_NC`, `R_ARM_MOVT_ABS`) to target instructions or data addresses.
- `arch_elf.c:up_relocateadd` - Returns `-ENOSYS` because `Elf32_Rela` addend relocations are not supported on 32-bit ARM.

## Invariants
- `arch_elf.c:up_checkarch` requires `ehdr->e_machine == EM_ARM`, `ehdr->e_ident[EI_CLASS] == ELFCLASS32`, matching endianness (`ELFDATA2MSB` or `ELFDATA2LSB`), and entry address alignment (16-bit aligned for `CONFIG_ARM_THUMB`, 32-bit aligned otherwise).
- `arch_elf.c:up_relocate` requires a non-`NULL` `sym` pointer for all relocation types except `R_ARM_NONE` and `R_ARM_V4BX`, and returns `-EINVAL` if branch or call offsets exceed instruction encoding ranges.

## Side Effects
- `arch_elf.c:up_relocate` mutates instruction words and data words in memory at `addr` to patch relocated symbol addresses and emits diagnostic logs via `berr` and `binfo`.

## Verification
- Run: `make test`
