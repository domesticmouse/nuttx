# rtl8721dx (`nuttx/arch/arm/include/rtl8721dx`)

## Overview
Hardware abstraction and architecture package for `rtl8721dx` under `nuttx/arch/arm/include/rtl8721dx`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:RTL8721DX_IRQ_RESERVED]`
- `[irq.h:RTL8721DX_IRQ_NMI]`
- `[irq.h:RTL8721DX_IRQ_HARDFAULT]`
- `[irq.h:RTL8721DX_IRQ_MEMFAULT]`
- `[irq.h:RTL8721DX_IRQ_BUSFAULT]`
- `[irq.h:RTL8721DX_IRQ_USAGEFAULT]`
- `[irq.h:RTL8721DX_IRQ_SVCALL]`
- `[irq.h:RTL8721DX_IRQ_DBGMONITOR]`
- `[irq.h:RTL8721DX_IRQ_PENDSV]`
- `[irq.h:RTL8721DX_IRQ_SYSTICK]`
- `[irq.h:RTL8721DX_IRQ_FIRST]`
- `[irq.h:RTL8721DX_IRQ_WIFI_FISR_FESR]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
