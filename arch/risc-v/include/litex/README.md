# litex (`nuttx/arch/risc-v/include/litex`)

## Overview
Hardware abstraction and architecture package for `litex` under `nuttx/arch/risc-v/include/litex`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[irq.h:LITEX_IRQ_UART0]`
- `[irq.h:LITEX_IRQ_TIMER0]`
- `[irq.h:LITEX_IRQ_ETHMAC]`
- `[irq.h:LITEX_IRQ_SDCARD]`
- `[irq.h:LITEX_IRQ_GPIO_BASE]`
- `[irq.h:LITEX_IRQ_GPIO_LENGTH]`
- `[irq.h:LITEX_IRQ_LAST]`
- `[irq.h:LITEX_NIRQ_GPIO]`
- `[irq.h:LITEX_FIRST_GPIOIRQ]`
- `[irq.h:LITEX_LAST_GPIOIRQ]`
- `[irq.h:NR_IRQS]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
