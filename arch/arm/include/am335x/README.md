# am335x (`nuttx/arch/arm/include/am335x`)

## Overview
Hardware abstraction and architecture package for `am335x` under `nuttx/arch/arm/include/am335x`, providing 3 header file(s) and 0 source file(s) (including `am335x_irq.h`, `chip.h`, `irq.h`).

## Interface
- `[am335x_irq.h:AM335X_IRQ_EMU]`
- `[am335x_irq.h:AM335X_IRQ_COMMTX]`
- `[am335x_irq.h:AM335X_IRQ_COMMRX]`
- `[am335x_irq.h:AM335X_IRQ_BENCH]`
- `[am335x_irq.h:AM335X_IRQ_ELM]`
- `[am335x_irq.h:AM335X_IRQ_NMI]`
- `[am335x_irq.h:AM335X_IRQ_L3DEBUG]`
- `[am335x_irq.h:AM335X_IRQ_L3APPINT]`
- `[am335x_irq.h:AM335X_IRQ_PRCM]`
- `[am335x_irq.h:AM335X_IRQ_EDMACOMP]`
- `[am335x_irq.h:AM335X_IRQ_EDMAMPERR]`
- `[am335x_irq.h:AM335X_IRQ_EDMAERR]`
- `[chip.h:TI_AM335X]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unrecognized AM335X chip
- `[irq.h:#error]` Compile-time guard: Unrecognized AM335X chip

## Side Effects
- None

## Verification
- Run: `make test`
