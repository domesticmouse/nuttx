# z16f (`nuttx/arch/z16/include/z16f`)

## Overview
Hardware abstraction and architecture package for `z16f` under `nuttx/arch/z16/include/z16f`, providing 3 header file(s) and 0 source file(s) (including `arch.h`, `chip.h`, `irq.h`).

## Interface
- `[irq.h:EI]`
- `[irq.h:DI]`
- `[irq.h:RI]`
- `[irq.h:SET_VECTOR]`
- `[irq.h:TDI]`
- `[irq.h:up_irq_save]`
- `[irq.h:up_irq_restore]`
- `[irq.h:xcptcontext]`
- `[irq.h:chipreg_t]`
- `[irq.h:Z16F_IRQ_IRQ0]`
- `[irq.h:Z16F_IRQ_ADC]`
- `[irq.h:Z16F_IRQ_SPI]`
- `[irq.h:Z16F_IRQ_I2C]`
- `[irq.h:Z16F_IRQ_UART0TX]`
- `[irq.h:Z16F_IRQ_UART0RX]`
- `[irq.h:Z16F_IRQ_TIMER0]`
- `[irq.h:Z16F_IRQ_TIMER1]`
- `[irq.h:Z16F_IRQ_TIMER2]`
- `[irq.h:Z16F_IRQ_IRQ1]`
- `[irq.h:Z16F_IRQ_P0AD]`
- `[irq.h:Z16F_IRQ_P1AD]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
