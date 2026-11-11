# cxd32xx (`nuttx/arch/arm/include/cxd32xx`)

## Overview
Hardware abstraction and architecture package for `cxd32xx` under `nuttx/arch/arm/include/cxd32xx`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:CXD32M4_SYSH_PRIORITY_MIN]`
- `[chip.h:CXD32M4_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:CXD32M4_SYSH_PRIORITY_MAX]`
- `[chip.h:CXD32M4_SYSH_PRIORITY_STEP]`
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:CXD32_IRQ_RESERVED]`
- `[irq.h:CXD32_IRQ_NMI]`
- `[irq.h:CXD32_IRQ_HARDFAULT]`
- `[irq.h:CXD32_IRQ_MEMFAULT]`
- `[irq.h:CXD32_IRQ_BUSFAULT]`
- `[irq.h:CXD32_IRQ_USAGEFAULT]`
- `[irq.h:CXD32_IRQ_SIGNVALUE]`
- `[irq.h:CXD32_IRQ_SVCALL]`
- `[irq.h:CXD32_IRQ_DBGMONITOR]`
- `[irq.h:CXD32_IRQ_PENDSV]`
- `[irq.h:CXD32_IRQ_SYSTICK]`
- `[irq.h:CXD32_IRQ_EXTINT]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
