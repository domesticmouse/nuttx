# hardware (`nuttx/arch/arm/src/stm32h7/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32h7/hardware`, providing 51 header file(s) and 0 source file(s) (including `stm32_adc.h`, `stm32_axi.h`, `stm32_bdma.h`, `stm32_dac.h`).

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
- `[stm32_axi.h:STM32_AXI_PERIPH_ID_4_OFFSET]`
- `[stm32_axi.h:STM32_AXI_PERIPH_ID_0_OFFSET]`
- `[stm32_axi.h:STM32_AXI_PERIPH_ID_1_OFFSET]`
- `[stm32_axi.h:STM32_AXI_PERIPH_ID_2_OFFSET]`
- `[stm32_axi.h:STM32_AXI_PERIPH_ID_3_OFFSET]`
- `[stm32_axi.h:STM32_AXI_COMP_ID_0_OFFSET]`
- `[stm32_axi.h:STM32_AXI_COMP_ID_1_OFFSET]`
- `[stm32_axi.h:STM32_AXI_COMP_ID_2_OFFSET]`
- `[stm32_axi.h:STM32_AXI_COMP_ID_3_OFFSET]`
- `[stm32_axi.h:STM32_AXI_TARG1_FN_MOD_ISS_BM_OFFSET]`
- `[stm32_axi.h:STM32_AXI_TARG2_FN_MOD_ISS_BM_OFFSET]`
- `[stm32_axi.h:STM32_AXI_TARG3_FN_MOD_ISS_BM_OFFSET]`
- `[stm32_bdma.h:STM32_BDMA_ISR_OFFSET]`
- `[stm32_bdma.h:STM32_BDMA_IFCR_OFFSET]`
- `[stm32_bdma.h:STM32_BDMACH_CCR_OFFSET]`
- `[stm32_bdma.h:STM32_BDMACH_CNDTR_OFFSET]`
- `[stm32_bdma.h:STM32_BDMACH_CPAR_OFFSET]`
- `[stm32_bdma.h:STM32_BDMACH_CM0AR_OFFSET]`

## Invariants
- `[stm32_dmamux.h:#error]` Compile-time guard: Unsupported STM32 H7 sub family
- `[stm32_flash.h:#error]` Compile-time guard: Unsupported STM32 H7 part
- `[stm32_gpio.h:#error]` Compile-time guard: Unsupported STM32 H7 part
- `[stm32_i2c.h:#error]` Compile-time guard: Unsupported STM32 H7 sub family
- `[stm32_memorymap.h:#error]` Compile-time guard: Unsupported STM32 H7 memory map
- `[stm32_pinmap.h:#error]` Compile-time guard: Unsupported STM32 H7 Pin map
- `[stm32_pwr.h:#error]` Compile-time guard: Unsupported STM32 H7 part
- `[stm32_rcc.h:#error]` Compile-time guard: Unsupported STM32 H7 part
- `[stm32_sdmmc.h:#error]` Compile-time guard: Unsupported STM32 H7 part
- `[stm32_spi.h:#error]` Compile-time guard: Unsupported STM32 H7 sub family
- `[stm32_syscfg.h:#error]` Compile-time guard: Unsupported STM32 H7 part

## Side Effects
- None

## Verification
- Run: `make test`
