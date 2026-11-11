# rtl8721f (`nuttx/arch/arm/include/rtl8721f`)

## Overview
Hardware abstraction and architecture package for `rtl8721f` under `nuttx/arch/arm/include/rtl8721f`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:RTL8721F_IRQ_RESERVED]`
- `[irq.h:RTL8721F_IRQ_NMI]`
- `[irq.h:RTL8721F_IRQ_HARDFAULT]`
- `[irq.h:RTL8721F_IRQ_MEMFAULT]`
- `[irq.h:RTL8721F_IRQ_BUSFAULT]`
- `[irq.h:RTL8721F_IRQ_USAGEFAULT]`
- `[irq.h:RTL8721F_IRQ_SECUREFAULT]`
- `[irq.h:RTL8721F_IRQ_SVCALL]`
- `[irq.h:RTL8721F_IRQ_DBGMONITOR]`
- `[irq.h:RTL8721F_IRQ_PENDSV]`
- `[irq.h:RTL8721F_IRQ_SYSTICK]`
- `[irq.h:RTL8721F_IRQ_FIRST]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
