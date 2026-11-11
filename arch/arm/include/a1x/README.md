# a1x (`nuttx/arch/arm/include/a1x`)

## Overview
Hardware abstraction and architecture package for `a1x` under `nuttx/arch/arm/include/a1x`, providing 3 header file(s) and 0 source file(s) (including `a10_irq.h`, `chip.h`, `irq.h`).

## Interface
- `[a10_irq.h:A1X_IRQ_NMI]`
- `[a10_irq.h:A1X_IRQ_POWER]`
- `[a10_irq.h:A1X_IRQ_BATTERY]`
- `[a10_irq.h:A1X_IRQ_BROWNOUT]`
- `[a10_irq.h:A1X_IRQ_UART0]`
- `[a10_irq.h:A1X_IRQ_UART1]`
- `[a10_irq.h:A1X_IRQ_UART2]`
- `[a10_irq.h:A1X_IRQ_UART3]`
- `[a10_irq.h:A1X_IRQ_IR0]`
- `[a10_irq.h:A1X_IRQ_IR1]`
- `[a10_irq.h:A1X_IRQ_TWI0]`
- `[a10_irq.h:A1X_IRQ_TWI1]`
- `[chip.h:ALLWINNER_A1X]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unrecognized A1X chip
- `[irq.h:#error]` Compile-time guard: Unrecognized A1X chip

## Side Effects
- None

## Verification
- Run: `make test`
