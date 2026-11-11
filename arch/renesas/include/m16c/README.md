# m16c (`nuttx/arch/renesas/include/m16c`)

## Overview
Hardware abstraction and architecture package for `m16c` under `nuttx/arch/renesas/include/m16c`, providing 5 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).

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
- `[irq.h:M16C_UNDEFINST_IRQ]`
- `[irq.h:M16C_OVERFLOW_IRQ]`
- `[irq.h:M16C_BRK_IRQ]`
- `[irq.h:M16C_ADDRMATCH_IRQ]`
- `[irq.h:M16C_SSTEP_IRQ]`
- `[irq.h:M16C_WDOG_IRQ]`
- `[irq.h:M16C_DBC_IRQ]`
- `[irq.h:M16C_NMI_IRQ]`
- `[irq.h:_LAST_FIXED]`
- `[limits.h:CHAR_BIT]`
- `[limits.h:SCHAR_MIN]`
- `[limits.h:SCHAR_MAX]`
- `[limits.h:UCHAR_MAX]`
- `[limits.h:CHAR_MIN]`
- `[limits.h:CHAR_MAX]`
- `[limits.h:SHRT_MIN]`
- `[limits.h:SHRT_MAX]`

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
