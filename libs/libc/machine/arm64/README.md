# ARM64 (AArch64) Machine Support (`libs/libc/machine/arm64`)

## Overview
Provides 64-bit ARM (AArch64) ELF header verification and instruction/data relocation, user-context (`ucontext_t`) creation and signal mask management, and `gprof` call-graph profiling (`_mcount`) with Pointer Authentication Code (PAC) stripping.

## Interface
- `arch_elf.c:up_checkarch` - Verifies that a 64-bit ELF header (`Elf64_Ehdr`) targets `EM_AARCH64`, `ELFCLASS64`, matches configured endianness (`CONFIG_ENDIAN_BIG`), and has a 4-byte aligned entry point.
- `arch_elf.c:up_relocate` - Handles `Elf64_Rel` relocations (returns `OK`).
- `arch_elf.c:up_relocateadd` - Applies `Elf64_Rela` AArch64 relocations (`R_AARCH64_NONE`, `R_AARCH64_ABS64`, `R_AARCH64_ABS32`, `R_AARCH64_ABS16`, `R_AARCH64_PREL64`, `R_AARCH64_PREL32`, `R_AARCH64_PREL16`, `R_AARCH64_MOVW_UABS_G0`..`G3`, `R_AARCH64_MOVW_SABS_G0`..`G2`, `R_AARCH64_ADR_PREL_LO21`, `R_AARCH64_ADR_PREL_PG_HI21`, `R_AARCH64_ADD_ABS_LO12_NC`, `R_AARCH64_LDST8/16/32/64/128_ABS_LO12_NC`, `R_AARCH64_JUMP26`, `R_AARCH64_CALL26`, `R_AARCH64_CONDBR19`, `R_AARCH64_TSTBR14`) with KASan tag resetting (`kasan_reset_tag`).
- `arch_makecontext.c:makecontext` - Initializes a `ucontext_t` structure (`ucp`) to invoke `func` with `argc` arguments (first 8 in `x0`-`x7`, remaining on the 16-byte aligned stack) and return via `arm64_ucontext_start`.
- `arch_makecontext.c:arm64_ucontext_getmask`, `arch_makecontext.c:arm64_ucontext_setmask`, `arch_makecontext.c:arm64_ucontext_swapmask` - Save, restore, and swap `ucp->uc_sigmask` via `sigprocmask`.
- `arch_mcount.c:_mcount` - Strips AArch64 PAC bits (`xpaclri`) from `frompc` and records call-graph edges via `mcount_internal`.

## Invariants
- `arch_elf.c:up_checkarch` requires `ehdr->e_machine == EM_AARCH64`, `ehdr->e_ident[EI_CLASS] == ELFCLASS64`, and `(ehdr->e_entry & 3) == 0`.
- `arch_elf.c:up_relocateadd` checks signed/unsigned immediate ranges for 14/16/19/21/26/32-bit relocations and returns `-ERANGE` on overflow.
- `arch_makecontext.c:makecontext` enforces `STACKFRAME_ALIGN` alignment on `ucp->uc_mcontext.sp`.

## Side Effects
- `arch_elf.c:up_relocateadd` mutates instructions and data in memory at `addr` (using `le32toh`/`htole32` for instruction encoding) and logs errors via `berr`.
- `arch_makecontext.c:arm64_ucontext_getmask`, `arch_makecontext.c:arm64_ucontext_setmask`, `arch_makecontext.c:arm64_ucontext_swapmask` query or modify the calling thread's blocked signal mask via `sigprocmask`.
- `arch_mcount.c:_mcount` updates global `gmon` profiling tables via `mcount_internal`.

## Verification
- Run: `make test`
