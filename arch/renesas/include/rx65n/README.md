# rx65n (`nuttx/arch/renesas/include/rx65n`)

## Overview
Hardware abstraction and architecture package for `rx65n` under `nuttx/arch/renesas/include/rx65n`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `iodefine.h`, `irq.h`).

## Interface
- `[inttypes.h:PRId8]`
- `[inttypes.h:PRId16]`
- `[inttypes.h:PRId32]`
- `[inttypes.h:PRId64]`
- `[inttypes.h:PRIdPTR]`
- `[inttypes.h:PRIi8]`
- `[inttypes.h:PRIi16]`
- `[inttypes.h:PRIi32]`
- `[inttypes.h:PRIi64]`
- `[inttypes.h:PRIiPTR]`
- `[inttypes.h:PRIo8]`
- `[inttypes.h:PRIo16]`
- `[iodefine.h:enum_ir_t]`
- `[iodefine.h:enum_dtce_t]`
- `[iodefine.h:enum_ier_t]`
- `[iodefine.h:enum_ipr_t]`
- `[iodefine.h:st_bsc_berclr_bit]`
- `[iodefine.h:un_bsc_berclr]`
- `[iodefine.h:st_bsc_beren_bit]`
- `[iodefine.h:un_bsc_beren]`
- `[iodefine.h:st_bsc_bersr1_bit]`
- `[iodefine.h:un_bsc_bersr1]`
- `[iodefine.h:st_bsc_bersr2_bit]`
- `[iodefine.h:un_bsc_bersr2]`
- `[iodefine.h:st_bsc_buspri_bit]`
- `[iodefine.h:un_bsc_buspri]`
- `[iodefine.h:st_bsc_cs0mod_bit]`
- `[iodefine.h:un_bsc_cs0mod]`
- `[iodefine.h:st_bsc_cs0wcr1_bit]`
- `[iodefine.h:un_bsc_cs0wcr1]`

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
