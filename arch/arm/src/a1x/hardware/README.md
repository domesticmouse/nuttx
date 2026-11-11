# hardware (`nuttx/arch/arm/src/a1x/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/a1x/hardware`, providing 8 header file(s) and 0 source file(s) (including `a10_memorymap.h`, `a10_piocfg.h`, `a1x_intc.h`, `a1x_memorymap.h`).

## Interface
- `[a10_memorymap.h:__CONCAT]`
- `[a10_memorymap.h:MKULONG]`
- `[a10_memorymap.h:A1X_INTMEM_PSECTION]`
- `[a10_memorymap.h:A1X_PERIPH_PSECTION]`
- `[a10_memorymap.h:A1X_SRAMC_PSECTION]`
- `[a10_memorymap.h:A1X_DE_PSECTION]`
- `[a10_memorymap.h:A1X_DDR_PSECTION]`
- `[a10_memorymap.h:A1X_BROM_PSECTION]`
- `[a10_memorymap.h:A1X_SRAMA1_OFFSET]`
- `[a10_memorymap.h:A1X_SRAMA2_OFFSET]`
- `[a10_memorymap.h:A1X_SRAMA3_OFFSET]`
- `[a10_memorymap.h:A1X_SRAMA4_OFFSET]`
- `[a10_piocfg.h:PIO_AC97_BCLK]`
- `[a10_piocfg.h:PIO_AC97_DI]`
- `[a10_piocfg.h:PIO_AC97_DO]`
- `[a10_piocfg.h:PIO_AC97_MCLK]`
- `[a10_piocfg.h:PIO_AC97_SYNC]`
- `[a10_piocfg.h:PIO_ATAA0]`
- `[a10_piocfg.h:PIO_ATAA1]`
- `[a10_piocfg.h:PIO_ATAA2]`
- `[a10_piocfg.h:PIO_ATACS0]`
- `[a10_piocfg.h:PIO_ATACS1]`
- `[a10_piocfg.h:PIO_ATAD0]`
- `[a10_piocfg.h:PIO_ATAD1]`
- `[a1x_intc.h:A1X_INTC_VECTOR_OFFSET]`
- `[a1x_intc.h:A1X_INTC_BASEADDR_OFFSET]`
- `[a1x_intc.h:A1X_INTC_PROTECT_OFFSET]`
- `[a1x_intc.h:A1X_INTC_NMICTRL_OFFSET]`
- `[a1x_intc.h:A1X_INTC_IRQ_PEND_OFFSET]`
- `[a1x_intc.h:A1X_INTC_IRQ_PEND0_OFFSET]`

## Invariants
- `[a10_memorymap.h:#error]` Compile-time guard: Only one of PGTABLE_BASE_PADDR or PGTABLE_BASE_VADDR is defined
- `[a1x_memorymap.h:#error]` Compile-time guard: Unrecognized A1X architecture
- `[a1x_piocfg.h:#error]` Compile-time guard: Unrecognized A1X architecture

## Side Effects
- None

## Verification
- Run: `make test`
