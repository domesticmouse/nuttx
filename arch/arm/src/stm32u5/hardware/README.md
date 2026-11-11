# hardware (`nuttx/arch/arm/src/stm32u5/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32u5/hardware`, providing 11 header file(s) and 0 source file(s) (including `stm32_dmasigmap.h`, `stm32_flash.h`, `stm32_i2c.h`, `stm32_memorymap.h`).

## Interface
- `[stm32_dmasigmap.h:GPDMA_REQ_ADC1]`
- `[stm32_dmasigmap.h:GPDMA_REQ_ADC4]`
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
- `[stm32_flash.h:CONFIG_STM32_FLASH_OVERRIDE_E]`
- `[stm32_flash.h:CONFIG_STM32_FLASH_CONFIG_C]`
- `[stm32_flash.h:CONFIG_STM32_FLASH_CONFIG_E]`
- `[stm32_flash.h:STM32_FLASH_NPAGES]`
- `[stm32_flash.h:STM32_FLASH_PAGESIZE]`
- `[stm32_flash.h:STM32_FLASH_SIZE]`
- `[stm32_flash.h:STM32_FLASH_ACR_OFFSET]`
- `[stm32_flash.h:STM32_FLASH_NSKEYR_OFFSET]`
- `[stm32_flash.h:STM32_FLASH_SECKEYR_OFFSET]`
- `[stm32_i2c.h:STM32_I2C_CR1_OFFSET]`
- `[stm32_i2c.h:STM32_I2C_CR2_OFFSET]`
- `[stm32_i2c.h:STM32_I2C_OAR1_OFFSET]`
- `[stm32_i2c.h:STM32_I2C_OAR2_OFFSET]`
- `[stm32_i2c.h:STM32_I2C_TIMINGR_OFFSET]`
- `[stm32_i2c.h:STM32_I2C_TIMEOUTR_OFFSET]`
- `[stm32_i2c.h:STM32_I2C_ISR_OFFSET]`
- `[stm32_i2c.h:STM32_I2C_ICR_OFFSET]`
- `[stm32_i2c.h:STM32_I2C_PECR_OFFSET]`

## Invariants
- `[stm32_flash.h:#error]` Compile-time guard: unknown flash configuration!
- `[stm32_memorymap.h:#error]` Compile-time guard: stm32_memorymap: unsupported STM32U5 memory map
- `[stm32_pinmap.h:#error]` Compile-time guard: Unsupported STM32U5 pin map
- `[stm32_spi.h:#error]` Compile-time guard: Unsupported STM32U5 chip

## Side Effects
- None

## Verification
- Run: `make test`
