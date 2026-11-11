# ARMv7-A Machine Support (`libs/libc/machine/arm/armv7-a`)

## Overview
Provides ACLE compatibility macro definitions, optimized assembly string/memory routines, and 32-bit ELF relocation support for ARMv7-A (Cortex-A) processors.

## Interface
- `acle-compat.h:__ARM_ARCH` - Backwards-compatible ARM C Language Extensions (ACLE) feature and ISA macros (`__ARM_ARCH`, `__ARM_ARCH_ISA_THUMB`, `__ARM_ARCH_ISA_ARM`, `__ARM_ARCH_PROFILE`, `__ARM_FEATURE_CLZ`, `__ARM_FEATURE_LDREX`, `__ARM_FEATURE_UNALIGNED`, `__ARM_FEATURE_DSP`, `__ARM_FEATURE_SIMD32`, `__ARM_FEATURE_QBIT`, `__ARM_FEATURE_SAT`).
- `arch_elf.c:up_checkarch` - Verifies that an `Elf32_Ehdr` header targets `EM_ARM`, `ELFCLASS32`, the configured endianness (`CONFIG_ENDIAN_BIG`), and aligned entry point (`CONFIG_ARM_THUMB`).
- `arch_elf.c:up_relocate` - Performs `Elf32_Rel` relocations for ARM and Thumb-2 instructions (`R_ARM_NONE`, `R_ARM_ABS32`, `R_ARM_PC24`, `R_ARM_CALL`, `R_ARM_JUMP24`, `R_ARM_MOVW_ABS_NC`, `R_ARM_MOVT_ABS`, `R_ARM_THM_CALL`, `R_ARM_THM_JUMP24`, `R_ARM_THM_MOVW_ABS_NC`, `R_ARM_THM_MOVT_ABS`, `R_ARM_PREL31`, `R_ARM_V4BX`, `R_ARM_GOT_PREL`, `R_ARM_REL32`, `R_ARM_TARGET1`).
- `arch_elf.c:up_relocateadd` - Returns `-ENOSYS` as `Elf32_Rela` relocations are unsupported.

## Invariants
- `arch_elf.c:up_checkarch` requires 32-bit `EM_ARM` ELF objects with 2-byte (`CONFIG_ARM_THUMB`) or 4-byte aligned entry points.
- `arch_elf.c:up_relocate` requires `sym != NULL` unless the relocation is `R_ARM_NONE` or `R_ARM_V4BX`, and validates that branch offsets fit within signed 24-bit/26-bit encoding limits.

## Side Effects
- `arch_elf.c:up_relocate` modifies instruction and data words in memory at `addr` (translating via `up_textheap_data_address` when applicable) and logs relocation diagnostics via `berr` and `binfo`.

## Verification
- Run: `make test`
