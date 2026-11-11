# RISC-V Machine Support (`libs/libc/machine/risc-v`)

## Overview
Provides 32-bit and 64-bit RISC-V (RV32/RV64) assembly register/FPU macros, optimized string/memory routines, and ELF header validation and relocation (supporting standard and RVC compressed instructions).

## Interface
- `asm.h:SZREG`, `asm.h:REG_S`, `asm.h:REG_L` - Register width and load/store instruction macros conditioned on `CONFIG_ARCH_RV64`.
- `asm.h:SZFREG`, `asm.h:FREG_S`, `asm.h:FREG_L` - Floating-point register width and load/store instruction macros conditioned on `CONFIG_ARCH_QPFPU`, `CONFIG_ARCH_DPFPU`, and `CONFIG_ARCH_FPU`.
- `arch_elf.c:up_checkarch` - Validates that an `Elf_Ehdr` header targets `EM_RISCV`, matches 32/64-bit class (`CONFIG_ARCH_64BIT`), matches endianness (`CONFIG_ENDIAN_BIG`), and has a 2-byte aligned entry point.
- `arch_elf.c:up_relocate` - Applies `Elf_Rel` relocations by delegating to `up_relocateadd` with zero addend.
- `arch_elf.c:up_relocateadd` - Applies `Elf_Rela` RISC-V relocations (`R_RISCV_NONE`, `R_RISCV_32`, `R_RISCV_64`, `R_RISCV_BRANCH`, `R_RISCV_JAL`, `R_RISCV_CALL`, `R_RISCV_CALL_PLT`, `R_RISCV_PCREL_HI20`, `R_RISCV_PCREL_LO12_I`, `R_RISCV_PCREL_LO12_S`, `R_RISCV_HI20`, `R_RISCV_LO12_I`, `R_RISCV_LO12_S`, `R_RISCV_RVC_JUMP`, `R_RISCV_RVC_BRANCH`, `R_RISCV_RELAX`, `R_RISCV_32_PCREL`).

## Invariants
- `arch_elf.c:up_checkarch` requires `ehdr->e_machine == EM_RISCV` and `(ehdr->e_entry & 1) == 0`.
- `arch_elf.c:up_relocateadd` accesses instruction words via 16-bit halfword loads/stores (`_get_val`, `_set_val`) because RVC instructions may only be 16-bit aligned, and enforces signed immediate range checks (`-EINVAL` on overflow).

## Side Effects
- `arch_elf.c:up_relocateadd` mutates instruction halfwords and data words at `addr`, executes `UP_ISB()` instruction synchronization barriers after instruction writes, records `PCREL_HI20` lookup entries in `arch_data`, and logs via `berr`/`binfo`.

## Verification
- Run: `make test`
