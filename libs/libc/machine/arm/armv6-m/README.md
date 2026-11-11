# ARMv6-M ELF Relocation (`libs/libc/machine/arm/armv6-m`)

## Overview
Provides architecture-specific 32-bit ELF header verification and Thumb-1/Thumb-2 relocation support for ARMv6-M (Cortex-M0/M0+/M1) targets.

## Interface
- `arch_elf.c:up_checkarch` - Verifies that an `Elf32_Ehdr` header targets `EM_ARM`, `ELFCLASS32`, and the configured endianness (`CONFIG_ENDIAN_BIG`).
- `arch_elf.c:up_relocate` - Applies `Elf32_Rel` relocations (`R_ARM_NONE`, `R_ARM_ABS32`, `R_ARM_THM_CALL`, `R_ARM_THM_JUMP24`, `R_ARM_THM_MOVW_ABS_NC`, `R_ARM_THM_MOVT_ABS`, `R_ARM_PREL31`, `R_ARM_V4BX`, `R_ARM_RELATIVE`, `R_ARM_JUMP_SLOT`) at `addr`.
- `arch_elf.c:up_relocateadd` - Returns `-ENOSYS` as `Elf32_Rela` relocations are not supported.

## Invariants
- `arch_elf.c:up_checkarch` requires `ehdr->e_machine == EM_ARM` and `ehdr->e_ident[EI_CLASS] == ELFCLASS32`.
- `arch_elf.c:up_relocate` requires `sym != NULL` for all relocation types other than `R_ARM_NONE`, `R_ARM_V4BX`, `R_ARM_RELATIVE`, and `R_ARM_JUMP_SLOT`, and enforces 22-bit Thumb branch offset bounds (`[-0x3ffffe, 0x3ffffe]`).

## Side Effects
- `arch_elf.c:up_relocate` patches 16-bit Thumb instruction halfwords and 32-bit data words in place at `addr` and logs errors via `berr`.

## Verification
- Run: `make test`
