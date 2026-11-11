# hardware (`nuttx/arch/arm/src/common/stm32/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/common/stm32/hardware`, providing 91 header file(s) and 0 source file(s) (including `stm32_adc.h`, `stm32_adc_v1.h`, `stm32_adc_v1l1.h`, `stm32_adc_v2.h`).

## Interface
- `[stm32_adc_v1.h:HAVE_IP_ADC_V1]`
- `[stm32_adc_v1.h:HAVE_BASIC_ADC]`
- `[stm32_adc_v1.h:HAVE_ADC_VBAT]`
- `[stm32_adc_v1.h:STM32_ADC1_OFFSET]`
- `[stm32_adc_v1.h:STM32_ADC2_OFFSET]`
- `[stm32_adc_v1.h:STM32_ADC3_OFFSET]`
- `[stm32_adc_v1.h:STM32_ADC_CMN_OFFSET]`
- `[stm32_adc_v1.h:STM32_ADC1_BASE]`
- `[stm32_adc_v1.h:STM32_ADC2_BASE]`
- `[stm32_adc_v1.h:STM32_ADC3_BASE]`
- `[stm32_adc_v1.h:STM32_ADCCMN_BASE]`
- `[stm32_adc_v1.h:STM32_ADC_SR_OFFSET]`
- `[stm32_adc_v1l1.h:HAVE_IP_ADC_V1]`
- `[stm32_adc_v1l1.h:HAVE_ADC_CLOCK_HSI]`
- `[stm32_adc_v1l1.h:HAVE_ADC_POWERDOWN]`
- `[stm32_adc_v1l1.h:STM32_ADC1_OFFSET]`
- `[stm32_adc_v1l1.h:STM32_ADC2_OFFSET]`
- `[stm32_adc_v1l1.h:STM32_ADC3_OFFSET]`
- `[stm32_adc_v1l1.h:STM32_ADC_CMN_OFFSET]`
- `[stm32_adc_v1l1.h:STM32_ADC1_BASE]`
- `[stm32_adc_v1l1.h:STM32_ADC2_BASE]`
- `[stm32_adc_v1l1.h:STM32_ADC3_BASE]`
- `[stm32_adc_v1l1.h:STM32_ADCCMN_BASE]`
- `[stm32_adc_v1l1.h:STM32_ADC_SR_OFFSET]`
- `[stm32_adc_v2.h:HAVE_IP_ADC_V2]`
- `[stm32_adc_v2.h:HAVE_ADC_VBAT]`
- `[stm32_adc_v2.h:HAVE_BASIC_ADC]`
- `[stm32_adc_v2.h:HAVE_ADC_CFGR2]`
- `[stm32_adc_v2.h:STM32_ADC1_OFFSET]`
- `[stm32_adc_v2.h:STM32_ADC2_OFFSET]`

## Invariants
- `[stm32_adc.h:#error]` Compile-time guard: Only one STM32 ADC IP version must be selected
- `[stm32_adc_v2.h:#error]` Compile-time guard: TODO
- `[stm32_can.h:#error]` Compile-time guard: Only one STM32 CAN IP version must be selected
- `[stm32_comp.h:#error]` Compile-time guard: Only one STM32 COMP IP version must be selected
- `[stm32_comp_v1v2.h:#error]` Compile-time guard: Device not supported.
- `[stm32_dac.h:#error]` Compile-time guard: Only one STM32 DAC IP version must be selected
- `[stm32_dac_v1v2.h:#error]` Compile-time guard: Only one STM32 DAC IP version must be selected
- `[stm32_dbgmcu.h:#error]` Compile-time guard: Unsupported STM32 DBGMCU
- `[stm32_dma.h:#error]` Compile-time guard: Only one STM32 DMA IP version must be selected
- `[stm32_dma_v1.h:#error]` Compile-time guard: Unsupported STM32 DMA v1
- `[stm32_dma_v1_7ch.h:#error]` Compile-time guard: Unknown DMA channel assignments
- `[stm32_dma_v1_8ch.h:#error]` Compile-time guard: Unknown DMA channel assignments

## Side Effects
- None

## Verification
- Run: `make test`
