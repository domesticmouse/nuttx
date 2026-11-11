# kl (`nuttx/arch/arm/include/kl`)

## Overview
Hardware abstraction and architecture package for `kl` under `nuttx/arch/arm/include/kl`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:KL_Z64]`
- `[chip.h:KL_FLASH_SIZE]`
- `[chip.h:KL_SRAM_SIZE]`
- `[chip.h:KL_NDMACH]`
- `[chip.h:KL_NUSBHOST]`
- `[chip.h:KL_NUSBOTG]`
- `[chip.h:KL_NUSBDEV]`
- `[chip.h:KL_NTOUCHIF]`
- `[chip.h:KL_NI2C]`
- `[chip.h:KL_NUART]`
- `[chip.h:KL_NSPI]`
- `[chip.h:KL_NI2S]`
- `[irq.h:KL_IRQ_RESERVED]`
- `[irq.h:KL_IRQ_NMI]`
- `[irq.h:KL_IRQ_HARDFAULT]`
- `[irq.h:KL_IRQ_SVCALL]`
- `[irq.h:KL_IRQ_PENDSV]`
- `[irq.h:KL_IRQ_SYSTICK]`
- `[irq.h:KL_IRQ_EXTINT]`
- `[irq.h:KL_IRQ_DMACH0]`
- `[irq.h:KL_IRQ_DMACH1]`
- `[irq.h:KL_IRQ_DMACH2]`
- `[irq.h:KL_IRQ_DMACH3]`
- `[irq.h:KL_IRQ_FTFA]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported Kinetis chip
- `[irq.h:#error]` Compile-time guard: No IRQ numbers for this Kinetis L part

## Side Effects
- None

## Verification
- Run: `make test`
