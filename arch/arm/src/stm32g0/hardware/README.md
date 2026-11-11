# hardware (`nuttx/arch/arm/src/stm32g0/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32g0/hardware`, providing 10 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32g0_dmamux.h`).

## Interface
- `[stm32_rcc.h:STM32_RCC_CR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_ICSCR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CFGR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_PLLCFG_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIER_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIFR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CICR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_IOPRSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHBRSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB1RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB2RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_IOPENR_OFFSET]`
- `[stm32g0_dmamux.h:DMAMUX1_REQ_GEN0]`
- `[stm32g0_dmamux.h:DMAMAP_DMA1_REQ_GEN0]`
- `[stm32g0_dmamux.h:DMAMAP_DMA2_REQ_GEN0]`
- `[stm32g0_dmamux.h:DMAMUX1_REQ_GEN1]`
- `[stm32g0_dmamux.h:DMAMAP_DMA1_REQ_GEN1]`
- `[stm32g0_dmamux.h:DMAMAP_DMA2_REQ_GEN1]`
- `[stm32g0_dmamux.h:DMAMUX1_REQ_GEN2]`
- `[stm32g0_dmamux.h:DMAMAP_DMA1_REQ_GEN2]`
- `[stm32g0_dmamux.h:DMAMAP_DMA2_REQ_GEN2]`
- `[stm32g0_dmamux.h:DMAMUX1_REQ_GEN3]`
- `[stm32g0_dmamux.h:DMAMAP_DMA1_REQ_GEN3]`
- `[stm32g0_dmamux.h:DMAMAP_DMA2_REQ_GEN3]`
- `[stm32g0_exti.h:STM32_NEXTI]`
- `[stm32g0_exti.h:STM32_EXTI_MASK]`
- `[stm32g0_exti.h:STM32_EXTI_BIT]`
- `[stm32g0_exti.h:STM32_EXTI_RTSR1_OFFSET]`
- `[stm32g0_exti.h:STM32_EXTI_FTSR1_OFFSET]`
- `[stm32g0_exti.h:STM32_EXTI_SWIER1_OFFSET]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
