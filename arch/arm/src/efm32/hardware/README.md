# hardware (`nuttx/arch/arm/src/efm32/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/efm32/hardware`, providing 32 header file(s) and 0 source file(s) (including `efm32_acmp.h`, `efm32_adc.h`, `efm32_aes.h`, `efm32_burtc.h`).

## Interface
- `[efm32_acmp.h:EFM32_ACMP_CTRL_OFFSET]`
- `[efm32_acmp.h:EFM32_ACMP_INPUTSEL_OFFSET]`
- `[efm32_acmp.h:EFM32_ACMP_STATUS_OFFSET]`
- `[efm32_acmp.h:EFM32_ACMP_IEN_OFFSET]`
- `[efm32_acmp.h:EFM32_ACMP_IF_OFFSET]`
- `[efm32_acmp.h:EFM32_ACMP_IFS_OFFSET]`
- `[efm32_acmp.h:EFM32_ACMP_IFC_OFFSET]`
- `[efm32_acmp.h:EFM32_ACMP_ROUTE_OFFSET]`
- `[efm32_acmp.h:EFM32_ACMP0_CTRL]`
- `[efm32_acmp.h:EFM32_ACMP0_INPUTSEL]`
- `[efm32_acmp.h:EFM32_ACMP0_STATUS]`
- `[efm32_acmp.h:EFM32_ACMP0_IEN]`
- `[efm32_adc.h:EFM32_ADC_CTRL_OFFSET]`
- `[efm32_adc.h:EFM32_ADC_CMD_OFFSET]`
- `[efm32_adc.h:EFM32_ADC_STATUS_OFFSET]`
- `[efm32_adc.h:EFM32_ADC_SINGLECTRL_OFFSET]`
- `[efm32_adc.h:EFM32_ADC_SCANCTRL_OFFSET]`
- `[efm32_adc.h:EFM32_ADC_IEN_OFFSET]`
- `[efm32_adc.h:EFM32_ADC_IF_OFFSET]`
- `[efm32_adc.h:EFM32_ADC_IFS_OFFSET]`
- `[efm32_adc.h:EFM32_ADC_IFC_OFFSET]`
- `[efm32_adc.h:EFM32_ADC_SINGLEDATA_OFFSET]`
- `[efm32_adc.h:EFM32_ADC_SCANDATA_OFFSET]`
- `[efm32_adc.h:EFM32_ADC_SINGLEDATAP_OFFSET]`
- `[efm32_aes.h:EFM32_AES_CTRL_OFFSET]`
- `[efm32_aes.h:EFM32_AES_CMD_OFFSET]`
- `[efm32_aes.h:EFM32_AES_STATUS_OFFSET]`
- `[efm32_aes.h:EFM32_AES_IEN_OFFSET]`
- `[efm32_aes.h:EFM32_AES_IF_OFFSET]`
- `[efm32_aes.h:EFM32_AES_IFS_OFFSET]`

## Invariants
- `[efm32_memorymap.h:#error]` Compile-time guard: Unsupported EFM32 memory map

## Side Effects
- None

## Verification
- Run: `make test`
