# hardware (`nuttx/arch/arm/src/s32k3xx/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/s32k3xx/hardware`, providing 46 header file(s) and 0 source file(s) (including `s32k344_pinmux.h`, `s32k3xx_adc.h`, `s32k3xx_axbs.h`, `s32k3xx_dcm.h`).

## Interface
- `[s32k344_pinmux.h:PIN_ADC0_MA0_1]`
- `[s32k344_pinmux.h:PIN_ADC0_MA0_2]`
- `[s32k344_pinmux.h:PIN_ADC0_MA0_3]`
- `[s32k344_pinmux.h:PIN_ADC0_MA0_4]`
- `[s32k344_pinmux.h:PIN_ADC0_MA1_1]`
- `[s32k344_pinmux.h:PIN_ADC0_MA1_2]`
- `[s32k344_pinmux.h:PIN_ADC0_MA1_3]`
- `[s32k344_pinmux.h:PIN_ADC0_MA1_4]`
- `[s32k344_pinmux.h:PIN_ADC0_MA2_1]`
- `[s32k344_pinmux.h:PIN_ADC0_MA2_2]`
- `[s32k344_pinmux.h:PIN_ADC0_MA2_3]`
- `[s32k344_pinmux.h:PIN_ADC0_MA2_4]`
- `[s32k3xx_adc.h:S32K3XX_ADC_MCR_OFFSET]`
- `[s32k3xx_adc.h:S32K3XX_ADC_MSR_OFFSET]`
- `[s32k3xx_adc.h:S32K3XX_ADC_ISR_OFFSET]`
- `[s32k3xx_adc.h:S32K3XX_ADC_CEOCFR0_OFFSET]`
- `[s32k3xx_adc.h:S32K3XX_ADC_CEOCFR1_OFFSET]`
- `[s32k3xx_adc.h:S32K3XX_ADC_CEOCFR2_OFFSET]`
- `[s32k3xx_adc.h:S32K3XX_ADC_IMR_OFFSET]`
- `[s32k3xx_adc.h:S32K3XX_ADC_CIMR0_OFFSET]`
- `[s32k3xx_adc.h:S32K3XX_ADC_CIMR1_OFFSET]`
- `[s32k3xx_adc.h:S32K3XX_ADC_CIMR2_OFFSET]`
- `[s32k3xx_adc.h:S32K3XX_ADC_WTISR_OFFSET]`
- `[s32k3xx_adc.h:S32K3XX_ADC_WTIMR_OFFSET]`
- `[s32k3xx_axbs.h:S32K3XX_AXBS_PRS0_OFFSET]`
- `[s32k3xx_axbs.h:S32K3XX_AXBS_CRS0_OFFSET]`
- `[s32k3xx_axbs.h:S32K3XX_AXBS_PRS1_OFFSET]`
- `[s32k3xx_axbs.h:S32K3XX_AXBS_CRS1_OFFSET]`
- `[s32k3xx_axbs.h:S32K3XX_AXBS_PRS2_OFFSET]`
- `[s32k3xx_axbs.h:S32K3XX_AXBS_CRS2_OFFSET]`

## Invariants
- `[s32k3xx_pinmux.h:#error]` Compile-time guard: No pin multiplexing for this S32K3xx part

## Side Effects
- None

## Verification
- Run: `make test`
