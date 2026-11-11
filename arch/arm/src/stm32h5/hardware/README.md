# hardware (`nuttx/arch/arm/src/stm32h5/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32h5/hardware`, providing 29 header file(s) and 0 source file(s) (including `stm32_adc.h`, `stm32_crc.h`, `stm32_crs.h`, `stm32_dac.h`).

## Interface
- `[stm32_adc.h:STM32_ADC1_OFFSET]`
- `[stm32_adc.h:STM32_ADC2_OFFSET]`
- `[stm32_adc.h:STM32_ADCCMN_OFFSET]`
- `[stm32_adc.h:STM32_ADC1_BASE]`
- `[stm32_adc.h:STM32_ADC2_BASE]`
- `[stm32_adc.h:STM32_ADC_ISR_OFFSET]`
- `[stm32_adc.h:STM32_ADC_IER_OFFSET]`
- `[stm32_adc.h:STM32_ADC_CR_OFFSET]`
- `[stm32_adc.h:STM32_ADC_CFGR_OFFSET]`
- `[stm32_adc.h:STM32_ADC_CFGR2_OFFSET]`
- `[stm32_adc.h:STM32_ADC_SMPR1_OFFSET]`
- `[stm32_adc.h:STM32_ADC_SMPR2_OFFSET]`
- `[stm32_crc.h:STM32_CRC_DR_OFFSET]`
- `[stm32_crc.h:STM32_CRC_IDR_OFFSET]`
- `[stm32_crc.h:STM32_CRC_CR_OFFSET]`
- `[stm32_crc.h:STM32_CRC_INIT_OFFSET]`
- `[stm32_crc.h:STM32_CRC_POL_OFFSET]`
- `[stm32_crc.h:STM32_CRC_DR]`
- `[stm32_crc.h:STM32_CRC_IDR]`
- `[stm32_crc.h:STM32_CRC_CR]`
- `[stm32_crc.h:STM32_CRC_INIT]`
- `[stm32_crc.h:STM32_CRC_POL]`
- `[stm32_crc.h:CRC_IDR_MASK]`
- `[stm32_crc.h:CRC_CR_RESET]`
- `[stm32_crs.h:STM32_CRS_CR_OFFSET]`
- `[stm32_crs.h:STM32_CRS_CFGR_OFFSET]`
- `[stm32_crs.h:STM32_CRS_ISR_OFFSET]`
- `[stm32_crs.h:STM32_CRS_ICR_OFFSET]`
- `[stm32_crs.h:STM32_CRS_CR]`
- `[stm32_crs.h:STM32_CRS_CFGR]`

## Invariants
- `[stm32_dmasigmap.h:#error]` Compile-time guard: Unsupported STM32H5 DMA signal map
- `[stm32_flash.h:#error]` Compile-time guard: Unsupported STM32 H5 flash
- `[stm32_i2c.h:#error]` Compile-time guard: Unsupported STM32 H5 I2C
- `[stm32_memorymap.h:#error]` Compile-time guard: Unsupported STM32 H5 memory map
- `[stm32_pinmap.h:#error]` Compile-time guard: Unsupported STM32 H5 pin map
- `[stm32_pwr.h:#error]` Compile-time guard: Unsupported STM32 H5 PWR
- `[stm32_rcc.h:#error]` Compile-time guard: Unsupported STM32 H5 rcc

## Side Effects
- None

## Verification
- Run: `make test`
