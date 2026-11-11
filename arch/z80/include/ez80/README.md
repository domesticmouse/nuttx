# ez80 (`nuttx/arch/z80/include/ez80`)

## Overview
Hardware abstraction and architecture package for `ez80` under `nuttx/arch/z80/include/ez80`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `io.h`, `irq.h`).

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
- `[io.h:outp]`
- `[io.h:inp]`
- `[irq.h:up_irq_save]`
- `[irq.h:up_irq_restore]`
- `[irq.h:up_irq_enable]`
- `[irq.h:xcptcontext]`
- `[irq.h:chipreg_t]`
- `[irq.h:EZ80_EMACRX_IRQ]`
- `[irq.h:EZ80_EMACTX_IRQ]`
- `[irq.h:EZ80_EMACSYS_IRQ]`
- `[irq.h:EZ80_PLL_IRQ]`
- `[irq.h:EZ80_FLASH_IRQ]`
- `[irq.h:EZ80_TIMER0_IRQ]`
- `[irq.h:EZ80_TIMER1_IRQ]`
- `[irq.h:EZ80_TIMER2_IRQ]`
- `[irq.h:EZ80_TIMER3_IRQ]`
- `[irq.h:EZ80_RTC_IRQ]`
- `[irq.h:EZ80_UART0_IRQ]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
