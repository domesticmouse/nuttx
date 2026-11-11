# z8 (`nuttx/arch/z80/include/z8`)

## Overview
Hardware abstraction and architecture package for `z8` under `nuttx/arch/z80/include/z8`, providing 5 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).

## Interface
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
- `[irq.h:up_irq_save]`
- `[irq.h:up_irq_restore]`
- `[irq.h:up_irq_enable]`
- `[irq.h:xcptcontext]`
- `[irq.h:chipreg_t]`
- `[irq.h:ENCORE_VECTORS]`
- `[irq.h:Z8_WDT_IRQ]`
- `[irq.h:Z8_TRAP_IRQ]`
- `[irq.h:Z8_TIMER2_IRQ]`
- `[irq.h:Z8_TIMER1_IRQ]`
- `[irq.h:Z8_TIMER0_IRQ]`
- `[irq.h:Z8_UART0_RX_IRQ]`
- `[irq.h:Z8_UART0_TX_IRQ]`
- `[irq.h:Z8_I2C_IRQ]`
- `[limits.h:CHAR_BIT]`
- `[limits.h:SCHAR_MIN]`
- `[limits.h:SCHAR_MAX]`
- `[limits.h:UCHAR_MAX]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Add IRQ support for Z8F family

## Side Effects
- None

## Verification
- Run: `make test`
