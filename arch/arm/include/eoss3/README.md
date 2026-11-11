# eoss3 (`nuttx/arch/arm/include/eoss3`)

## Overview
Hardware abstraction and architecture package for `eoss3` under `nuttx/arch/arm/include/eoss3`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:EOSS3_IRQ_RESERVED]`
- `[irq.h:EOSS3_IRQ_NMI]`
- `[irq.h:EOSS3_IRQ_HARDFAULT]`
- `[irq.h:EOSS3_IRQ_MEMFAULT]`
- `[irq.h:EOSS3_IRQ_BUSFAULT]`
- `[irq.h:EOSS3_IRQ_USAGEFAULT]`
- `[irq.h:EOSS3_IRQ_SVCALL]`
- `[irq.h:EOSS3_IRQ_DBGMONITOR]`
- `[irq.h:EOSS3_IRQ_PENDSV]`
- `[irq.h:EOSS3_IRQ_SYSTICK]`
- `[irq.h:EOSS3_IRQ_EXTINT]`
- `[irq.h:EOSS3_IRQ_SW2]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
