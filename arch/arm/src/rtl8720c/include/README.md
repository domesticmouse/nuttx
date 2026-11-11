# include (`nuttx/arch/arm/src/rtl8720c/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/arm/src/rtl8720c/include`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[irq.h:NVIC_IRQ_NMI]`
- `[irq.h:NVIC_IRQ_HARDFAULT]`
- `[irq.h:NVIC_IRQ_MEMFAULT]`
- `[irq.h:NVIC_IRQ_BUSFAULT]`
- `[irq.h:NVIC_IRQ_USAGEFAULT]`
- `[irq.h:NVIC_IRQ_SVCALL]`
- `[irq.h:NVIC_IRQ_DBGMONITOR]`
- `[irq.h:NVIC_IRQ_PENDSV]`
- `[irq.h:NVIC_IRQ_SYSTICK]`
- `[irq.h:NVIC_IRQ_FIRST]`
- `[irq.h:NVIC_IRQ_WLAN]`
- `[irq.h:NR_IRQS]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
