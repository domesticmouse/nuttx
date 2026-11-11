# ARMv8-M Machine Support (`libs/libc/machine/arm/armv8-m`)

## Overview
Provides ACLE compatibility definitions, Thumb-2 optimized string/memory routines, and 32-bit ELF relocation support for ARMv8-M (Cortex-M23/M33/M55/M85) processors.

## Interface
- `acle-compat.h:__ARM_ARCH` - Defines ACLE architecture and feature macros (`__ARM_ARCH`, `__ARM_ARCH_ISA_THUMB`, `__ARM_ARCH_PROFILE`, `__ARM_FEATURE_CLZ`, `__ARM_FEATURE_LDREX`, `__ARM_FEATURE_UNALIGNED`, `__ARM_FEATURE_DSP`, `__ARM_FEATURE_SIMD32`).
- `arch_elf.c:up_checkarch` - Verifies that an `Elf32_Ehdr` header targets `EM_ARM`, `ELFCLASS32`, and matches system endianness (`CONFIG_ENDIAN_BIG`).
- `arch_elf.c:up_relocate` - Applies `Elf32_Rel` Thumb-2 and data relocations (`R_ARM_NONE`, `R_ARM_ABS32`, `R_ARM_THM_CALL`, `R_ARM_THM_JUMP24`, `R_ARM_THM_MOVW_ABS_NC`, `R_ARM_THM_MOVT_ABS`, `R_ARM_THM_MOVW_PREL_NC`, `R_ARM_THM_MOVT_PREL`, `R_ARM_PREL31`, `R_ARM_GOT_PREL`, `R_ARM_REL32`, `R_ARM_TARGET1`, `R_ARM_RELATIVE`, `R_ARM_JUMP_SLOT`, `R_ARM_GLOB_DAT`, `R_ARM_FUNCDESC`).
- `arch_elf.c:up_relocateadd` - Returns `-ENOSYS` because `Elf32_Rela` relocations are not used on ARMv8-M.

## Invariants
- `arch_elf.c:up_relocate` requires `sym != NULL` except for `R_ARM_NONE`, `R_ARM_V4BX`, `R_ARM_RELATIVE`, `R_ARM_JUMP_SLOT`, and `R_ARM_GLOB_DAT`.
- `arch_elf.c:up_relocate` requires Thumb branch target addresses to have bit 0 set and to reside within the signed 24-bit displacement range.

## Side Effects
- `arch_elf.c:up_relocate` patches instruction halfwords and data words in memory at `addr` (resolving via `up_textheap_data_address` when in text heap) and logs errors via `berr`.

## Verification
- Run: `make test`
