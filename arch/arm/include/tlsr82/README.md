# tlsr82 (`nuttx/arch/arm/include/tlsr82`)

## Overview
Hardware abstraction and architecture package for `tlsr82` under `nuttx/arch/arm/include/tlsr82`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[irq.h:xcptcontext]`
- `[irq.h:_REG_BASE_ADDR]`
- `[irq.h:_REG_ADDR8]`
- `[irq.h:_REG_ADDR32]`
- `[irq.h:_IRQ_MASK_REG]`
- `[irq.h:_IRQ_EN_REG]`
- `[irq.h:NR_TIMER0_IRQ]`
- `[irq.h:NR_TIMER1_IRQ]`
- `[irq.h:NR_TIMER2_IRQ]`
- `[irq.h:NR_USB_PWDN_IRQ]`
- `[irq.h:NR_DMA_IRQ]`
- `[irq.h:NR_DMA_FIFO_IRQ]`
- `[irq.h:NR_UART_IRQ]`

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
