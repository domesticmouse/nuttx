# nuc1xx (`nuttx/arch/arm/include/nuc1xx`)

## Overview
Hardware abstraction and architecture package for `nuc1xx` under `nuttx/arch/arm/include/nuc1xx`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `nuc120_irq.h`).

## Interface
- `[chip.h:NUC100]`
- `[chip.h:NUC_LOW]`
- `[chip.h:NUC_FLASH]`
- `[chip.h:NUC_SRAM]`
- `[chip.h:NUC_NIO]`
- `[chip.h:NUC_NTIMERS]`
- `[chip.h:NUC_NPDMA]`
- `[chip.h:NUC_NUARTS]`
- `[chip.h:NUC_NSPI]`
- `[chip.h:NUC_NI2C]`
- `[chip.h:NUC_NUSB]`
- `[chip.h:NUC_NLIN]`
- `[irq.h:NUC_IRQ_RESERVED]`
- `[irq.h:NUC_IRQ_NMI]`
- `[irq.h:NUC_IRQ_HARDFAULT]`
- `[irq.h:NUC_IRQ_SVCALL]`
- `[irq.h:NUC_IRQ_PENDSV]`
- `[irq.h:NUC_IRQ_SYSTICK]`
- `[irq.h:NUC_IRQ_INTERRUPT]`
- `[nuc120_irq.h:NUC_IRQ_BOD]`
- `[nuc120_irq.h:NUC_IRQ_WDT]`
- `[nuc120_irq.h:NUC_IRQ_EINT0]`
- `[nuc120_irq.h:NUC_IRQ_EINT1]`
- `[nuc120_irq.h:NUC_IRQ_GPAB]`
- `[nuc120_irq.h:NUC_IRQ_GPCDE]`
- `[nuc120_irq.h:NUC_IRQ_PWMA]`
- `[nuc120_irq.h:NUC_IRQ_PWMB]`
- `[nuc120_irq.h:NUC_IRQ_TMR0]`
- `[nuc120_irq.h:NUC_IRQ_TMR1]`
- `[nuc120_irq.h:NUC_IRQ_TMR2]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unrecognized NUC1XX chip
- `[irq.h:#error]` Compile-time guard: Unrecognized/unsupported NUC chip

## Side Effects
- None

## Verification
- Run: `make test`
