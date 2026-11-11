# lpc2378 (`nuttx/arch/arm/include/lpc2378`)

## Overview
Hardware abstraction and architecture package for `lpc2378` under `nuttx/arch/arm/include/lpc2378`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).

## Interface
- `[irq.h:up_attach_vector]`
- `[irq.h:up_detach_vector]`
- `[irq.h:WDT_IRQ]`
- `[irq.h:RESERVED_IRQ]`
- `[irq.h:DBGCOMMRX_IRQ]`
- `[irq.h:DBGCOMMTX_IRQ]`
- `[irq.h:TIMER0_IRQ]`
- `[irq.h:TIMER1_IRQ]`
- `[irq.h:UART0_IRQ]`
- `[irq.h:UART1_IRQ]`
- `[irq.h:PWM0_IRQ]`
- `[irq.h:I2C0_IRQ]`
- `[irq.h:SPI0_IRQ]`
- `[irq.h:SSP0_IRQ]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
