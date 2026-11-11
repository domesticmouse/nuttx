# z80 (`nuttx/arch/z80/include/z80`)

## Overview
Hardware abstraction and architecture package for `z80` under `nuttx/arch/z80/include/z80`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `chip.h`, `inttypes.h`, `io.h`).

## Interface
- `[chip.h:Z80_C_FLAG]`
- `[chip.h:Z80_N_FLAG]`
- `[chip.h:Z80_PV_FLAG]`
- `[chip.h:Z80_H_FLAG]`
- `[chip.h:Z80_Z_FLAG]`
- `[chip.h:Z80_S_FLAG]`
- `[inttypes.h:PRId8]`
- `[inttypes.h:PRId16]`
- `[inttypes.h:PRId32]`
- `[inttypes.h:PRIdPTR]`
- `[inttypes.h:PRIi8]`
- `[inttypes.h:PRIi16]`
- `[inttypes.h:PRIi32]`
- `[inttypes.h:PRIiPTR]`
- `[inttypes.h:PRIo8]`
- `[inttypes.h:PRIo16]`
- `[inttypes.h:PRIo32]`
- `[inttypes.h:PRIoPTR]`
- `[io.h:outp]`
- `[io.h:inp]`
- `[irq.h:up_irq_enable]`
- `[irq.h:xcptcontext]`
- `[irq.h:chipreg_t]`
- `[irq.h:Z80_RST0]`
- `[irq.h:Z80_RST1]`
- `[irq.h:Z80_RST2]`
- `[irq.h:Z80_RST3]`
- `[irq.h:Z80_RST4]`
- `[irq.h:Z80_RST5]`
- `[irq.h:Z80_RST6]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
