# hardware (`nuttx/arch/arm/src/at32/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/at32/hardware`, providing 26 header file(s) and 0 source file(s) (including `at32_adc.h`, `at32_adc_v1.h`, `at32_can.h`, `at32_dbgmcu.h`).

## Interface
- `[at32_adc_v1.h:HAVE_IP_ADC_V1]`
- `[at32_adc_v1.h:HAVE_BASIC_ADC]`
- `[at32_adc_v1.h:HAVE_ADC_VBAT]`
- `[at32_adc_v1.h:AT32_ADC1_OFFSET]`
- `[at32_adc_v1.h:AT32_ADC2_OFFSET]`
- `[at32_adc_v1.h:AT32_ADC3_OFFSET]`
- `[at32_adc_v1.h:AT32_ADC_CMN_OFFSET]`
- `[at32_adc_v1.h:AT32_ADC1_BASE]`
- `[at32_adc_v1.h:AT32_ADC2_BASE]`
- `[at32_adc_v1.h:AT32_ADC3_BASE]`
- `[at32_adc_v1.h:AT32_ADCCMN_BASE]`
- `[at32_adc_v1.h:AT32_ADC_SR_OFFSET]`
- `[at32_can.h:CAN_TXMBOX1]`
- `[at32_can.h:CAN_TXMBOX2]`
- `[at32_can.h:CAN_TXMBOX3]`
- `[at32_can.h:CAN_RXMBOX1]`
- `[at32_can.h:CAN_RXMBOX2]`
- `[at32_can.h:CAN_NFILTERS]`
- `[at32_can.h:AT32_CAN_MCTRL_OFFSET]`
- `[at32_can.h:AT32_CAN_MSTS_OFFSET]`
- `[at32_can.h:AT32_CAN_TSTS_OFFSET]`
- `[at32_can.h:AT32_CAN_RF_OFFSET]`
- `[at32_can.h:AT32_CAN_RF0_OFFSET]`
- `[at32_dbgmcu.h:AT32_DEBUG_IDCODE]`
- `[at32_dbgmcu.h:AT32_DEBUG_CTRL]`
- `[at32_dbgmcu.h:AT32_DEBUG_APB1_PAUSE]`
- `[at32_dbgmcu.h:AT32_DEBUG_APB2_PAUSE]`
- `[at32_dbgmcu.h:AT32_DEBUG_SER_ID]`
- `[at32_dbgmcu.h:DEBUG_IDCODE_DEVID_SHIFT]`
- `[at32_dbgmcu.h:DEBUG_IDCODE_DEVID_MASK]`

## Invariants
- `[at32_adc.h:#error]` Compile-time guard: Only one AT32 ADC IP version must be selected
- `[at32_dmamux.h:#error]` Compile-time guard: Unsupported AT32 sub family
- `[at32_memorymap.h:#error]` Compile-time guard: Unsupported AT32 memory map
- `[at32_pinmap.h:#error]` Compile-time guard: No pinmap file for this AT32 chip

## Side Effects
- None

## Verification
- Run: `make test`
