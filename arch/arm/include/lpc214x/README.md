# lpc214x (`nuttx/arch/arm/include/lpc214x`)

## Overview
Hardware abstraction and architecture package for `lpc214x` under `nuttx/arch/arm/include/lpc214x`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).

## Interface
- `[irq.h:up_attach_vector]`
- `[irq.h:up_detach_vector]`
- `[irq.h:LPC214X_WDT_IRQ]`
- `[irq.h:LPC214X_RESERVED_IRQ]`
- `[irq.h:LPC214X_DBGCOMMRX_IRQ]`
- `[irq.h:LPC214X_DBGCOMMTX_IRQ]`
- `[irq.h:LPC214X_TIMER0_IRQ]`
- `[irq.h:LPC214X_TIMER1_IRQ]`
- `[irq.h:LPC214X_UART0_IRQ]`
- `[irq.h:LPC214X_UART1_IRQ]`
- `[irq.h:LPC214X_PWM0_IRQ]`
- `[irq.h:LPC214X_I2C0_IRQ]`
- `[irq.h:LPC214X_SPI0_IRQ]`
- `[irq.h:LPC214X_SPI1_IRQ]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
