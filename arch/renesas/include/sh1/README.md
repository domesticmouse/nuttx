# sh1 (`nuttx/arch/renesas/include/sh1`)

## Overview
Hardware abstraction and architecture package for `sh1` under `nuttx/arch/renesas/include/sh1`, providing 5 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).

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
- `[irq.h:SH1_INVINSTR_IRQ]`
- `[irq.h:SH1_INVSLOT_IRQ]`
- `[irq.h:SH1_BUSERR_IRQ]`
- `[irq.h:SH1_DMAERR_IRQ]`
- `[irq.h:SH1_NMI_IRQ]`
- `[irq.h:SH1_USRBRK_IRQ]`
- `[irq.h:SH1_TRAP_IRQBASE]`
- `[irq.h:SH1_TRAP0_IRQ]`
- `[irq.h:SH1_TRAP1_IRQ]`
- `[irq.h:SH1_TRAP2_IRQ]`
- `[irq.h:SH1_TRAP3_IRQ]`
- `[irq.h:SH1_TRAP4_IRQ]`
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
