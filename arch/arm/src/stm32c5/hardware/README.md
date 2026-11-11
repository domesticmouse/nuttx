# hardware (`nuttx/arch/arm/src/stm32c5/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32c5/hardware`, providing 9 header file(s) and 0 source file(s) (including `stm32_dmasigmap.h`, `stm32_flash.h`, `stm32_memorymap.h`, `stm32_pinmap.h`).

## Interface
- `[stm32_dmasigmap.h:LPDMA_REQ_ADC1]`
- `[stm32_dmasigmap.h:LPDMA_REQ_ADC2]`
- `[stm32_dmasigmap.h:LPDMA_REQ_TIM6_UPD]`
- `[stm32_dmasigmap.h:LPDMA_REQ_TIM7_UPD]`
- `[stm32_dmasigmap.h:LPDMA_REQ_SPI1_RX]`
- `[stm32_dmasigmap.h:LPDMA_REQ_SPI1_TX]`
- `[stm32_dmasigmap.h:LPDMA_REQ_SPI2_RX]`
- `[stm32_dmasigmap.h:LPDMA_REQ_SPI2_TX]`
- `[stm32_dmasigmap.h:LPDMA_REQ_SPI3_RX]`
- `[stm32_dmasigmap.h:LPDMA_REQ_SPI3_TX]`
- `[stm32_dmasigmap.h:LPDMA_REQ_I2C1_RX]`
- `[stm32_dmasigmap.h:LPDMA_REQ_I2C1_TX]`
- `[stm32c5xx_flash.h:STM32_FLASH_NPAGES]`
- `[stm32c5xx_flash.h:STM32_FLASH_PAGESIZE]`
- `[stm32c5xx_flash.h:STM32_FLASH_SIZE]`
- `[stm32c5xx_flash.h:STM32_FLASH_ACR_OFFSET]`
- `[stm32c5xx_flash.h:STM32_FLASH_KEYR_OFFSET]`
- `[stm32c5xx_flash.h:STM32_FLASH_OPTKEYR_OFFSET]`
- `[stm32c5xx_flash.h:STM32_FLASH_OPSR_OFFSET]`
- `[stm32c5xx_flash.h:STM32_FLASH_OPTCR_OFFSET]`
- `[stm32c5xx_flash.h:STM32_FLASH_SR_OFFSET]`
- `[stm32c5xx_flash.h:STM32_FLASH_CR_OFFSET]`
- `[stm32c5xx_flash.h:STM32_FLASH_CCR_OFFSET]`
- `[stm32c5xx_flash.h:STM32_FLASH_PRIVCFGR_OFFSET]`
- `[stm32c5xx_memorymap.h:STM32_CODE_BASE]`
- `[stm32c5xx_memorymap.h:STM32_SRAM_BASE]`
- `[stm32c5xx_memorymap.h:STM32_PERIPH_BASE]`
- `[stm32c5xx_memorymap.h:STM32_CORTEX_BASE]`
- `[stm32c5xx_memorymap.h:STM32_REGION_MASK]`
- `[stm32c5xx_memorymap.h:STM32_IS_SRAM]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
