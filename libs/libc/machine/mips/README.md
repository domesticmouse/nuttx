# MIPS Machine Support (`libs/libc/machine/mips`)

## Overview
Provides 32-bit MIPS ELF header verification and instruction/data relocation (`R_MIPS_*`), including deferred paired `R_MIPS_HI16`/`R_MIPS_LO16` addend resolution.

## Interface
- `arch_elf.c:up_checkarch` - Validates that an `Elf32_Ehdr` header targets `EM_MIPS`, `ELFCLASS32`, configured endianness (`CONFIG_ENDIAN_BIG`), and a 4-byte aligned entry point.
- `arch_elf.c:up_relocate` - Applies `Elf_Rel` MIPS relocations (`R_MIPS_NONE`, `R_MIPS_16`, `R_MIPS_32`, `R_MIPS_26`, `R_MIPS_HI16`, `R_MIPS_LO16`, `R_MIPS_GPREL16`, `R_MIPS_LITERAL`, `R_MIPS_GOT16`, `R_MIPS_PC16`, `R_MIPS_CALL16`) using `arch_elfdata_t` to queue `R_MIPS_HI16` locations until matching `R_MIPS_LO16` entries are processed.
- `arch_elf.c:up_relocateadd` - Returns `-ENOSYS` because `Elf_Rela` relocations are not supported on 32-bit MIPS.

## Invariants
- `arch_elf.c:up_checkarch` requires `ehdr->e_machine == EM_MIPS`, `ehdr->e_ident[EI_CLASS] == ELFCLASS32`, and `(ehdr->e_entry & 3) == 0`.
- `arch_elf.c:up_relocate` requires `arch_data != NULL` and `sym != NULL` (for relocations other than `R_MIPS_NONE`).

## Side Effects
- `arch_elf.c:up_relocate` mutates MIPS instructions and data words at `addr`, dynamically allocates/frees `struct mips_hi16_s` nodes via `kmm_malloc`/`kmm_free` inside `arch_data`, and logs diagnostics via `berr` and `binfo`.

## Verification
- Run: `make test`
