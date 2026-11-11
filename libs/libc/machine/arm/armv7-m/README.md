# ARMv7-M Machine Support (`libs/libc/machine/arm/armv7-m`)

## Overview
Provides ACLE compatibility definitions, Thumb-2 optimized string/memory routines, and 32-bit ELF relocation support (including FDPIC/GOT relocations) for ARMv7-M (Cortex-M3/M4/M7) microcontrollers.

## Interface
- `acle-compat.h:__ARM_ARCH` - Defines ACLE architecture and feature macros (`__ARM_ARCH`, `__ARM_ARCH_ISA_THUMB`, `__ARM_ARCH_PROFILE`, `__ARM_FEATURE_CLZ`, `__ARM_FEATURE_LDREX`, `__ARM_FEATURE_UNALIGNED`, `__ARM_FEATURE_DSP`, `__ARM_FEATURE_SIMD32`).
- `arch_elf.c:up_checkarch` - Validates that an `Elf32_Ehdr` header targets `EM_ARM`, `ELFCLASS32`, and matches system endianness (`CONFIG_ENDIAN_BIG`).
- `arch_elf.c:up_relocate` - Applies `Elf32_Rel` Thumb-2 and data relocations (`R_ARM_NONE`, `R_ARM_ABS32`, `R_ARM_THM_CALL`, `R_ARM_THM_JUMP24`, `R_ARM_THM_MOVW_ABS_NC`, `R_ARM_THM_MOVT_ABS`, `R_ARM_THM_MOVW_PREL_NC`, `R_ARM_THM_MOVT_PREL`, `R_ARM_PREL31`, `R_ARM_GOT_PREL`, `R_ARM_REL32`, `R_ARM_TARGET1`, `R_ARM_RELATIVE`, `R_ARM_JUMP_SLOT`, `R_ARM_GLOB_DAT`, `R_ARM_FUNCDESC`).
- `arch_elf.c:up_relocateadd` - Returns `-ENOSYS` because `Elf32_Rela` relocations are not used on ARMv7-M.

## Invariants
- `arch_elf.c:up_relocate` requires `sym != NULL` except for `R_ARM_NONE`, `R_ARM_V4BX`, `R_ARM_RELATIVE`, `R_ARM_JUMP_SLOT`, and `R_ARM_GLOB_DAT`.
- `arch_elf.c:up_relocate` validates that Thumb-2 `BL`/`B.W` branch targets have bit 0 set (Thumb state) and fit within the 24-bit signed branch range.

## Side Effects
- `arch_elf.c:up_relocate` mutates instruction halfwords and data words at `addr` (using `up_textheap_data_address` when `up_textheap_heapmember` holds) and logs errors via `berr`.

## Verification
- Run: `make test`
