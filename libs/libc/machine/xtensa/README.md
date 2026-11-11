# Xtensa Machine Support (`libs/libc/machine/xtensa`)

## Overview
Provides Xtensa assembly helper macros, `gprof` call-graph profiling (`_mcount`), and 32-bit Xtensa ELF header validation and relocation routines.

## Interface
- `xtensa_asm.h:MASK0`, `xtensa_asm.h:MASK1`, `xtensa_asm.h:MASK2`, `xtensa_asm.h:MASK3` - Endianness-aware (`XCHAL_HAVE_BE`) byte mask macros and `src_b`/`ssa8` assembly shift macros.
- `arch_mcount.c:_mcount` - Captures return address register `a0`, reconstructs windowed ABI upper PC bits when `!__XTENSA_CALL0_ABI__`, and invokes `mcount_internal`.
- `arch_elf.c:up_checkarch` - Verifies that an `Elf32_Ehdr` header targets `EM_XTENSA`, `ELFCLASS32`, and little-endian (`ELFDATA2LSB`).
- `arch_elf.c:up_relocate` - Handles `R_XTENSA_NONE` `Elf32_Rel` relocations and rejects unsupported types with `-EINVAL`.
- `arch_elf.c:up_relocateadd` - Applies `Elf32_Rela` Xtensa relocations (`R_XTENSA_NONE`, `R_XTENSA_32`, `R_XTENSA_ASM_EXPAND`, `R_XTENSA_SLOT0_OP` for `L32R` instructions).

## Invariants
- `arch_elf.c:up_checkarch` requires 32-bit little-endian `EM_XTENSA` ELF objects (`CONFIG_ENDIAN_BIG` is unsupported).
- `arch_elf.c:up_relocateadd` verifies that `R_XTENSA_SLOT0_OP` (`L32R`) target addresses lie within the negative 18-bit word-aligned PC-relative range (`0xfffc0000 | (imm << 2)`).

## Side Effects
- `arch_elf.c:up_relocateadd` modifies instruction bytes and data words via `up_textheap_data_address(addr)` and logs via `berr`/`bwarn`.
- `arch_mcount.c:_mcount` updates profiling state via `mcount_internal`.

## Verification
- Run: `make test`
