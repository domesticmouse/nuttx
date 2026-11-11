# hardware (`nuttx/arch/arm/src/stm32l4/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32l4/hardware`, providing 46 header file(s) and 0 source file(s) (including `stm32_rcc.h`, `stm32l4_adc.h`, `stm32l4_can.h`, `stm32l4_comp.h`).

## Interface
- `[stm32l4_adc.h:STM32_ADC_ISR_OFFSET]`
- `[stm32l4_adc.h:STM32_ADC_IER_OFFSET]`
- `[stm32l4_adc.h:STM32_ADC_CR_OFFSET]`
- `[stm32l4_adc.h:STM32_ADC_CFGR_OFFSET]`
- `[stm32l4_adc.h:STM32_ADC_CFGR2_OFFSET]`
- `[stm32l4_adc.h:STM32_ADC_SMPR1_OFFSET]`
- `[stm32l4_adc.h:STM32_ADC_SMPR2_OFFSET]`
- `[stm32l4_adc.h:STM32_ADC_TR1_OFFSET]`
- `[stm32l4_adc.h:STM32_ADC_TR2_OFFSET]`
- `[stm32l4_adc.h:STM32_ADC_TR3_OFFSET]`
- `[stm32l4_adc.h:STM32_ADC_SQR1_OFFSET]`
- `[stm32l4_adc.h:STM32_ADC_SQR2_OFFSET]`
- `[stm32l4_can.h:CAN_TXMBOX1]`
- `[stm32l4_can.h:CAN_TXMBOX2]`
- `[stm32l4_can.h:CAN_TXMBOX3]`
- `[stm32l4_can.h:CAN_RXMBOX1]`
- `[stm32l4_can.h:CAN_RXMBOX2]`
- `[stm32l4_can.h:CAN_NFILTERS]`
- `[stm32l4_can.h:STM32_CAN_MCR_OFFSET]`
- `[stm32l4_can.h:STM32_CAN_MSR_OFFSET]`
- `[stm32l4_can.h:STM32_CAN_TSR_OFFSET]`
- `[stm32l4_can.h:STM32_CAN_RFR_OFFSET]`
- `[stm32l4_can.h:STM32_CAN_RF0R_OFFSET]`
- `[stm32l4_can.h:STM32_CAN_RF1R_OFFSET]`
- `[stm32l4_comp.h:STM32_COMP_CSR_OFFSET]`
- `[stm32l4_comp.h:STM32_COMP1_CSR_OFFSET]`
- `[stm32l4_comp.h:STM32_COMP2_CSR_OFFSET]`
- `[stm32l4_comp.h:STM32_COMP_CSR]`
- `[stm32l4_comp.h:STM32_COMP1_CSR]`
- `[stm32l4_comp.h:STM32_COMP2_CSR]`

## Invariants
- `[stm32_rcc.h:#error]` Compile-time guard: Unsupported STM32L4 chip
- `[stm32l4_flash.h:#error]` Compile-time guard: unknown flash configuration!
- `[stm32l4_pinmap.h:#error]` Compile-time guard: Unsupported STM32 L4 pin map
- `[stm32l4_syscfg.h:#error]` Compile-time guard: Unsupported STM32 L4 chip

## Side Effects
- None

## Verification
- Run: `make test`
