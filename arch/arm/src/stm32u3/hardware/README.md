# hardware (`nuttx/arch/arm/src/stm32u3/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32u3/hardware`, providing 9 header file(s) and 0 source file(s) (including `stm32_dmasigmap.h`, `stm32_flash.h`, `stm32_memorymap.h`, `stm32_pinmap.h`).

## Interface
- `[stm32_dmasigmap.h:GPDMA_REQ_ADC1]`
- `[stm32_dmasigmap.h:GPDMA_REQ_ADC2]`
- `[stm32_dmasigmap.h:GPDMA_REQ_DAC1_CH1]`
- `[stm32_dmasigmap.h:GPDMA_REQ_DAC1_CH2]`
- `[stm32_dmasigmap.h:GPDMA_REQ_TIM6_UP]`
- `[stm32_dmasigmap.h:GPDMA_REQ_TIM7_UP]`
- `[stm32_dmasigmap.h:GPDMA_REQ_SPI1_RX]`
- `[stm32_dmasigmap.h:GPDMA_REQ_SPI1_TX]`
- `[stm32_dmasigmap.h:GPDMA_REQ_SPI2_RX]`
- `[stm32_dmasigmap.h:GPDMA_REQ_SPI2_TX]`
- `[stm32_dmasigmap.h:GPDMA_REQ_SPI3_RX]`
- `[stm32_dmasigmap.h:GPDMA_REQ_SPI3_TX]`
- `[stm32_memorymap.h:STM32_CODE_BASE]`
- `[stm32_memorymap.h:STM32_SRAM_BASE]`
- `[stm32_memorymap.h:STM32_PERIPH_BASE]`
- `[stm32_memorymap.h:STM32_EXTRAM_BASE]`
- `[stm32_memorymap.h:STM32_OCTOSPI1_BANK]`
- `[stm32_memorymap.h:STM32_EPPB_BASE]`
- `[stm32_memorymap.h:STM32_CORTEX_BASE]`
- `[stm32_memorymap.h:STM32_REGION_MASK]`
- `[stm32_memorymap.h:STM32_IS_SRAM]`
- `[stm32_memorymap.h:STM32_BOOT_BASE]`
- `[stm32_memorymap.h:STM32_FLASH_BASE]`
- `[stm32_memorymap.h:STM32_SYSMEM_BASE]`
- `[stm32u3c5xx_pinmap.h:GPIO_ADC1_IN1_1]`
- `[stm32u3c5xx_pinmap.h:GPIO_ADC1_IN2_1]`
- `[stm32u3c5xx_pinmap.h:GPIO_ADC1_IN3_1]`
- `[stm32u3c5xx_pinmap.h:GPIO_ADC1_IN4_1]`
- `[stm32u3c5xx_pinmap.h:GPIO_ADC1_IN5_1]`
- `[stm32u3c5xx_pinmap.h:GPIO_ADC1_IN6_1]`

## Invariants
- `[stm32_flash.h:#error]` Compile-time guard: Unsupported STM32U3 FLASH
- `[stm32_pinmap.h:#error]` Compile-time guard: Unsupported STM32U3 pin map
- `[stm32u3xx_flash.h:#error]` Compile-time guard: Unsupported STM32U3 FLASH geometry
- `[stm32u3xx_syscfg.h:#error]` Compile-time guard: Unsupported STM32U3 SYSCFG

## Side Effects
- None

## Verification
- Run: `make test`
