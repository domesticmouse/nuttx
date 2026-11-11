# z180 (`nuttx/arch/z80/include/z180`)

## Overview
Hardware abstraction and architecture package for `z180` under `nuttx/arch/z80/include/z180`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `chip.h`, `inttypes.h`, `io.h`).

## Interface
- `[arch.h:arch_addrenv_t]`
- `[chip.h:Z180_C_FLAG]`
- `[chip.h:Z180_N_FLAG]`
- `[chip.h:Z180_PV_FLAG]`
- `[chip.h:Z180_H_FLAG]`
- `[chip.h:Z180_Z_FLAG]`
- `[chip.h:Z180_S_FLAG]`
- `[chip.h:HAVE_Z8X180]`
- `[chip.h:HAVE]`
- `[chip.h:HAVE_SERIALIO]`
- `[chip.h:HAVE_NTIMERS16]`
- `[chip.h:HAVE_NCTCS]`
- `[chip.h:HAVE_NDMA]`
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
- `[irq.h:z180_cbr_s]`
- `[irq.h:xcptcontext]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unrecognized/undefined Z180 chip

## Side Effects
- None

## Verification
- Run: `make test`
