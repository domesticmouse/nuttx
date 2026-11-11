# kinetis (`nuttx/arch/arm/include/kinetis`)

## Overview
Hardware abstraction and architecture package for `kinetis` under `nuttx/arch/arm/include/kinetis`, providing 14 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `kinetis_dma.h`, `kinetis_dmamux.h`).

## Interface
- `[chip.h:KINETIS_K20]`
- `[chip.h:KINETIS_FLASH_SIZE]`
- `[chip.h:KINETIS_FLEXMEM_SIZE]`
- `[chip.h:KINETIS_SRAM_SIZE]`
- `[irq.h:KINETIS_IRQ_RESERVED]`
- `[irq.h:KINETIS_IRQ_NMI]`
- `[irq.h:KINETIS_IRQ_HARDFAULT]`
- `[irq.h:KINETIS_IRQ_MEMFAULT]`
- `[irq.h:KINETIS_IRQ_BUSFAULT]`
- `[irq.h:KINETIS_IRQ_USAGEFAULT]`
- `[irq.h:KINETIS_IRQ_SVCALL]`
- `[irq.h:KINETIS_IRQ_DBGMONITOR]`
- `[irq.h:KINETIS_IRQ_PENDSV]`
- `[irq.h:KINETIS_IRQ_SYSTICK]`
- `[irq.h:KINETIS_IRQ_FIRST]`
- `[kinetis_dma.h:KINETIS_DMA_VERSION_UKN]`
- `[kinetis_dma.h:KINETIS_DMA_VERSION_01]`
- `[kinetis_dma.h:KINETIS_DMA_VERSION_02]`
- `[kinetis_dma.h:KINETIS_DMA_VERSION]`
- `[kinetis_dma.h:KINETIS_DMA_HAS_ES_ERRCHN]`
- `[kinetis_dma.h:KINETIS_DMA_HAS_ES_ERRCHN_BITS]`
- `[kinetis_dma.h:KINETIS_DMA_HAS_CEEI_CEEI_BITS]`
- `[kinetis_dma.h:KINETIS_DMA_HAS_SEEI_SEEI_BITS]`
- `[kinetis_dmamux.h:KINETIS_DMAMUX_VERSION_UKN]`
- `[kinetis_dmamux.h:KINETIS_DMAMUX_VERSION_01]`
- `[kinetis_dmamux.h:KINETIS_DMAMUX_VERSION_02]`
- `[kinetis_dmamux.h:KINETIS_DMAMUX_VERSION]`
- `[kinetis_dmamux.h:KINETIS_DMAMUX_HAS_MONOTONIC_CHCFG]`
- `[kinetis_k20irq.h:KINETIS_IRQ_DMACH0]`
- `[kinetis_k20irq.h:KINETIS_IRQ_DMACH1]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported Kinetis chip
- `[irq.h:#error]` Compile-time guard: No IRQ numbers for this Kinetis K part
- `[kinetis_lpuart.h:#error]` Compile-time guard: Unsupported Kinetis chip
- `[kinetis_mcg.h:#error]` Compile-time guard: Unsupported Kinetis chip
- `[kinetis_pmc.h:#error]` Compile-time guard: Unsupported Kinetis chip
- `[kinetis_sim.h:#error]` Compile-time guard: Unsupported Kinetis chip

## Side Effects
- None

## Verification
- Run: `make test`
