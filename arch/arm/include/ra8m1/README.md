# ra8m1 (`nuttx/arch/arm/include/ra8m1`)

## Overview
Hardware abstraction and architecture package for `ra8m1` under `nuttx/arch/arm/include/ra8m1`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `ra8m1_irq.h`).

## Interface
- `[chip.h:RA_NSCI_B]`
- `[chip.h:RA_NGPT]`
- `[chip.h:RA_NIIC]`
- `[chip.h:RA_RAM_SIZE]`
- `[chip.h:RA_FLASH_SIZE]`
- `[chip.h:RA_DATA_FLASH_SIZE]`
- `[chip.h:RA_ITCM_SIZE]`
- `[chip.h:RA_DTCM_SIZE]`
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
- `[irq.h:NR_IRQS]`
- `[ra8m1_irq.h:ra_icu_event_irq_e]`
- `[ra8m1_irq.h:RA_IRQ_FIRST]`
- `[ra8m1_irq.h:RA_IRQ_IELSR0]`
- `[ra8m1_irq.h:RA_IRQ_IELSR1]`
- `[ra8m1_irq.h:RA_IRQ_IELSR2]`
- `[ra8m1_irq.h:RA_IRQ_IELSR3]`
- `[ra8m1_irq.h:RA_IRQ_IELSR4]`
- `[ra8m1_irq.h:RA_IRQ_IELSR5]`
- `[ra8m1_irq.h:RA_IRQ_IELSR6]`
- `[ra8m1_irq.h:RA_IRQ_IELSR7]`
- `[ra8m1_irq.h:RA_IRQ_IELSR8]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported RA8M1 chip
- `[irq.h:#error]` Compile-time guard: Unrecognized RA architecture

## Side Effects
- None

## Verification
- Run: `make test`
