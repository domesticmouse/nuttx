# ARMv8-R Machine Support (`libs/libc/machine/arm/armv8-r`)

## Overview
Provides ACLE compatibility definitions, optimized assembly string/memory functions, and 32-bit ELF relocation support for ARMv8-R (Cortex-R52/R82 AArch32) real-time processors.

## Interface
- `acle-compat.h:__ARM_ARCH` - Defines ACLE architecture and feature macros (`__ARM_ARCH`, `__ARM_ARCH_ISA_THUMB`, `__ARM_ARCH_ISA_ARM`, `__ARM_ARCH_PROFILE`, `__ARM_FEATURE_CLZ`, `__ARM_FEATURE_LDREX`, `__ARM_FEATURE_UNALIGNED`, `__ARM_FEATURE_DSP`, `__ARM_FEATURE_SIMD32`).
- `arch_elf.c:up_checkarch` - Verifies that an `Elf32_Ehdr` header targets `EM_ARM`, `ELFCLASS32`, configured endianness (`CONFIG_ENDIAN_BIG`), and aligned entry point (`CONFIG_ARM_THUMB`).
- `arch_elf.c:up_relocate` - Applies `Elf32_Rel` relocations (`R_ARM_NONE`, `R_ARM_ABS32`, `R_ARM_PC24`, `R_ARM_CALL`, `R_ARM_JUMP24`, `R_ARM_MOVW_ABS_NC`, `R_ARM_MOVT_ABS`, `R_ARM_THM_CALL`, `R_ARM_THM_JUMP24`, `R_ARM_THM_MOVW_ABS_NC`, `R_ARM_THM_MOVT_ABS`, `R_ARM_PREL31`, `R_ARM_V4BX`).
- `arch_elf.c:up_relocateadd` - Returns `-ENOSYS` as `Elf32_Rela` relocations are unsupported.

## Invariants
- `arch_elf.c:up_checkarch` requires `ehdr->e_entry` to be 2-byte aligned under `CONFIG_ARM_THUMB` or 4-byte aligned otherwise.
- `arch_elf.c:up_relocate` requires `sym != NULL` for all relocations except `R_ARM_NONE` and `R_ARM_V4BX`, and validates branch displacement bounds before patching.

## Side Effects
- `arch_elf.c:up_relocate` mutates instruction and data words in memory at `addr` and outputs diagnostics via `berr` and `binfo`.

## Verification
- Run: `make test`
