# avr (`nuttx/arch/avr/include/avr`)

## Overview
Hardware abstraction and architecture package for `avr` under `nuttx/arch/avr/include/avr`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `avr.h`, `inttypes.h`, `irq.h`).

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
- `[irq.h:xcptcontext]`
- `[irq.h:REG_SPH]`
- `[irq.h:REG_SPL]`
- `[irq.h:REG_R27]`
- `[irq.h:REG_R26]`
- `[irq.h:REG_R31]`
- `[irq.h:REG_R30]`
- `[irq.h:REG_R29]`
- `[irq.h:REG_R28]`
- `[irq.h:REG_R23]`
- `[irq.h:REG_R22]`
- `[irq.h:REG_R21]`
- `[irq.h:REG_R20]`
- `[limits.h:CHAR_BIT]`
- `[limits.h:SCHAR_MIN]`
- `[limits.h:SCHAR_MAX]`
- `[limits.h:UCHAR_MAX]`
- `[limits.h:CHAR_MIN]`

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
