# samd5e5 (`nuttx/arch/arm/include/samd5e5`)

## Overview
Hardware abstraction and architecture package for `samd5e5` under `nuttx/arch/arm/include/samd5e5`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `samd5e5_irq.h`).

## Interface
- `[chip.h:SAMD5E5_FLASH_SIZE]`
- `[chip.h:SAMD5E5_SRAM_SIZE]`
- `[chip.h:SAMD5E5_NSERCOM]`
- `[chip.h:SAMD5E5_NTC]`
- `[chip.h:SAMD5E5_NTCCOMP]`
- `[chip.h:SAMD5E5_NTCC24]`
- `[chip.h:SAMD5E5_NSDHC]`
- `[chip.h:SAMD5E5_NDMACHAN]`
- `[chip.h:SAMD5E5_PCCSIZE]`
- `[chip.h:SAMD5E5_NCCL]`
- `[chip.h:SAMD5E5_NEVTCHAN]`
- `[chip.h:SAMD5E5_NADC0CHAN]`
- `[irq.h:SAM_IRQ_RESERVED]`
- `[irq.h:SAM_IRQ_NMI]`
- `[irq.h:SAM_IRQ_HARDFAULT]`
- `[irq.h:SAM_IRQ_MEMFAULT]`
- `[irq.h:SAM_IRQ_BUSFAULT]`
- `[irq.h:SAM_IRQ_USAGEFAULT]`
- `[irq.h:SAM_IRQ_SVCALL]`
- `[irq.h:SAM_IRQ_DBGMONITOR]`
- `[irq.h:SAM_IRQ_PENDSV]`
- `[irq.h:SAM_IRQ_SYSTICK]`
- `[irq.h:SAM_IRQ_EXTINT]`
- `[samd5e5_irq.h:SAM_IRQ_PM]`
- `[samd5e5_irq.h:SAM_IRQ_MCLK]`
- `[samd5e5_irq.h:SAM_IRQ_XOSC0]`
- `[samd5e5_irq.h:SAM_IRQ_XOSC1]`
- `[samd5e5_irq.h:SAM_IRQ_DFLL]`
- `[samd5e5_irq.h:SAM_IRQ_DPLL0]`
- `[samd5e5_irq.h:SAM_IRQ_DPLL1]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unrecognized SAMD5x/Ex chip
- `[irq.h:#error]` Compile-time guard: Unsupported SAMD5/E5 family

## Side Effects
- None

## Verification
- Run: `make test`
