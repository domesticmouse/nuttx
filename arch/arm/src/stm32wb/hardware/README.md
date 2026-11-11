# hardware (`nuttx/arch/arm/src/stm32wb/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32wb/hardware`, providing 17 header file(s) and 0 source file(s) (including `stm32_rcc.h`, `stm32wb_crs.h`, `stm32wb_dma.h`, `stm32wb_dmamux.h`).

## Interface
- `[stm32_rcc.h:STM32_RCC_CR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_ICSCR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CFGR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_PLLCFG_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_PLLSAI1CFG_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIER_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIFR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CICR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_SMPSCR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB1RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB2RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB3RSTR_OFFSET]`
- `[stm32wb_crs.h:STM32_CRS_CR_OFFSET]`
- `[stm32wb_crs.h:STM32_CRS_CFGR_OFFSET]`
- `[stm32wb_crs.h:STM32_CRS_ISR_OFFSET]`
- `[stm32wb_crs.h:STM32_CRS_ICR_OFFSET]`
- `[stm32wb_crs.h:STM32_CRS_CR]`
- `[stm32wb_crs.h:STM32_CRS_CFGR]`
- `[stm32wb_crs.h:STM32_CRS_ISR]`
- `[stm32wb_crs.h:STM32_CRS_ICR]`
- `[stm32wb_crs.h:CRS_CR_SYNCOKIE]`
- `[stm32wb_crs.h:CRS_CR_SYNCWARNIE]`
- `[stm32wb_crs.h:CRS_CR_ERRIE]`
- `[stm32wb_crs.h:CRS_CR_ESYNCIE]`
- `[stm32wb_dma.h:DMA1]`
- `[stm32wb_dma.h:DMA2]`
- `[stm32wb_dma.h:STM32_DMA_ISR_OFFSET]`
- `[stm32wb_dma.h:STM32_DMA_IFCR_OFFSET]`
- `[stm32wb_dma.h:STM32_DMACHAN_OFFSET]`
- `[stm32wb_dma.h:STM32_DMACHAN1_OFFSET]`

## Invariants
- `[stm32wb_flash.h:#error]` Compile-time guard: Flash size not defined
- `[stm32wb_pinmap.h:#error]` Compile-time guard: Unsupported STM32WB Pin map

## Side Effects
- None

## Verification
- Run: `make test`
