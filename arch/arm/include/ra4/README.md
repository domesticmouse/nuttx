# ra4 (`nuttx/arch/arm/include/ra4`)

## Overview
Hardware abstraction and architecture package for `ra4` under `nuttx/arch/arm/include/ra4`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `ra4m1_irq.h`).

## Interface
- `[chip.h:RA_FLASH_SIZE]`
- `[chip.h:RA_SRAM0_SIZE]`
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:RA_IRQ_RESERVED]`
- `[irq.h:RA_IRQ_NMI]`
- `[irq.h:RA_IRQ_HARDFAULT]`
- `[irq.h:RA_IRQ_MEMFAULT]`
- `[irq.h:RA_IRQ_BUSFAULT]`
- `[irq.h:RA_IRQ_USAGEFAULT]`
- `[irq.h:RA_IRQ_SVCALL]`
- `[irq.h:RA_IRQ_DBGMONITOR]`
- `[irq.h:RA_IRQ_PENDSV]`
- `[irq.h:RA_IRQ_SYSTICK]`
- `[irq.h:RA_IRQ_FIRST]`
- `[irq.h:NR_IRQS]`
- `[ra4m1_irq.h:RA_IRQ_IELSR0]`
- `[ra4m1_irq.h:RA_IRQ_IELSR1]`
- `[ra4m1_irq.h:RA_IRQ_IELSR2]`
- `[ra4m1_irq.h:RA_IRQ_IELSR3]`
- `[ra4m1_irq.h:RA_IRQ_IELSR4]`
- `[ra4m1_irq.h:RA_IRQ_IELSR5]`
- `[ra4m1_irq.h:RA_IRQ_IELSR6]`
- `[ra4m1_irq.h:RA_IRQ_IELSR7]`
- `[ra4m1_irq.h:RA_IRQ_IELSR8]`
- `[ra4m1_irq.h:RA_IRQ_IELSR9]`
- `[ra4m1_irq.h:RA_IRQ_IELSR10]`
- `[ra4m1_irq.h:RA_IRQ_IELSR11]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unrecognized RA architecture

## Side Effects
- None

## Verification
- Run: `make test`
