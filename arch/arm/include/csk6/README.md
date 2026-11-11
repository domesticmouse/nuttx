# csk6 (`nuttx/arch/arm/include/csk6`)

## Overview
Hardware abstraction and architecture package for `csk6` under `nuttx/arch/arm/include/csk6`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:CSK6_IRQ_RESERVED]`
- `[irq.h:CSK6_IRQ_NMI]`
- `[irq.h:CSK6_IRQ_HARDFAULT]`
- `[irq.h:CSK6_IRQ_MEMFAULT]`
- `[irq.h:CSK6_IRQ_BUSFAULT]`
- `[irq.h:CSK6_IRQ_USAGEFAULT]`
- `[irq.h:CSK6_IRQ_SVCALL]`
- `[irq.h:CSK6_IRQ_DBGMONITOR]`
- `[irq.h:CSK6_IRQ_PENDSV]`
- `[irq.h:CSK6_IRQ_SYSTICK]`
- `[irq.h:CSK6_IRQ_FIRST]`
- `[irq.h:CSK6_NEXTINT]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
