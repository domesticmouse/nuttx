# hardware (`nuttx/arch/arm/src/imxrt/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/imxrt/hardware`, providing 37 header file(s) and 0 source file(s) (including `imxrt_adc.h`, `imxrt_adc_etc.h`, `imxrt_adc_ver1.h`, `imxrt_adc_ver2.h`).

## Subdirectories & Boundaries
- `rt102x`: [./rt102x/README.md](./rt102x/README.md) - Hardware abstraction and architecture package for `rt102x` under `nuttx/arch/arm/src/imxrt/hardware/rt102x`, providing 7 header file(s) and 0 source file(s) (including `imxrt102x_ccm.h`, `imxrt102x_dmamux.h`, `imxrt102x_gpio.h`, `imxrt102x_iomuxc.h`).
- `rt105x`: [./rt105x/README.md](./rt105x/README.md) - Hardware abstraction and architecture package for `rt105x` under `nuttx/arch/arm/src/imxrt/hardware/rt105x`, providing 7 header file(s) and 0 source file(s) (including `imxrt105x_ccm.h`, `imxrt105x_dmamux.h`, `imxrt105x_gpio.h`, `imxrt105x_iomuxc.h`).
- `rt106x`: [./rt106x/README.md](./rt106x/README.md) - Hardware abstraction and architecture package for `rt106x` under `nuttx/arch/arm/src/imxrt/hardware/rt106x`, providing 7 header file(s) and 0 source file(s) (including `imxrt106x_ccm.h`, `imxrt106x_dmamux.h`, `imxrt106x_gpio.h`, `imxrt106x_iomuxc.h`).
- `rt117x`: [./rt117x/README.md](./rt117x/README.md) - Hardware abstraction and architecture package for `rt117x` under `nuttx/arch/arm/src/imxrt/hardware/rt117x`, providing 18 header file(s) and 0 source file(s) (including `imxrt117x_anadig.h`, `imxrt117x_caam.h`, `imxrt117x_ccm.h`, `imxrt117x_dcdc.h`).
- `rt118x`: [./rt118x/README.md](./rt118x/README.md) - Hardware abstraction and architecture package for `rt118x` under `nuttx/arch/arm/src/imxrt/hardware/rt118x`, providing 15 header file(s) and 0 source file(s) (including `imxrt118x_anadig.h`, `imxrt118x_blkctrl.h`, `imxrt118x_ccm.h`, `imxrt118x_dmamux.h`).

## Interface
- `[imxrt_adc_etc.h:TRIG_OFFSET]`
- `[imxrt_adc_etc.h:IRQ_OFFSET]`
- `[imxrt_adc_etc.h:CHAIN_OFFSET]`
- `[imxrt_adc_etc.h:RESULT_OFFSET]`
- `[imxrt_adc_etc.h:IMXRT_ADC_ETC_CTRL_OFFSET]`
- `[imxrt_adc_etc.h:IMXRT_ADC_ETC_DONE01_IRQ_OFFSET]`
- `[imxrt_adc_etc.h:IMXRT_ADC_ETC_DONE2_ERR_IRQ_OFFSET]`
- `[imxrt_adc_etc.h:IMXRT_ADC_ETC_DMA_CTRL_OFFSET]`
- `[imxrt_adc_etc.h:IMXRT_ADC_ETC_TRIG_CTRL_OFFSET]`
- `[imxrt_adc_etc.h:IMXRT_ADC_ETC_TRIG_COUNTER_OFFSET]`
- `[imxrt_adc_etc.h:IMXRT_ADC_ETC_TRIG_CHAIN_OFFSET]`
- `[imxrt_adc_etc.h:IMXRT_ADC_ETC_TRIG_RESULT_OFFSET]`
- `[imxrt_adc_ver1.h:IMXRT_ADC_HC0_OFFSET]`
- `[imxrt_adc_ver1.h:IMXRT_ADC_HC1_OFFSET]`
- `[imxrt_adc_ver1.h:IMXRT_ADC_HC2_OFFSET]`
- `[imxrt_adc_ver1.h:IMXRT_ADC_HC3_OFFSET]`
- `[imxrt_adc_ver1.h:IMXRT_ADC_HC4_OFFSET]`
- `[imxrt_adc_ver1.h:IMXRT_ADC_HC5_OFFSET]`
- `[imxrt_adc_ver1.h:IMXRT_ADC_HC6_OFFSET]`
- `[imxrt_adc_ver1.h:IMXRT_ADC_HC7_OFFSET]`
- `[imxrt_adc_ver1.h:IMXRT_ADC_HS_OFFSET]`
- `[imxrt_adc_ver1.h:IMXRT_ADC_R0_OFFSET]`
- `[imxrt_adc_ver1.h:IMXRT_ADC_R1_OFFSET]`
- `[imxrt_adc_ver1.h:IMXRT_ADC_R2_OFFSET]`
- `[imxrt_adc_ver2.h:IMXRT_LPADC_VERID_OFFSET]`
- `[imxrt_adc_ver2.h:IMXRT_LPADC_PARAM_OFFSET]`
- `[imxrt_adc_ver2.h:IMXRT_LPADC_CTRL_OFFSET]`
- `[imxrt_adc_ver2.h:IMXRT_LPADC_STAT_OFFSET]`
- `[imxrt_adc_ver2.h:IMXRT_LPADC_IE_OFFSET]`
- `[imxrt_adc_ver2.h:IMXRT_LPADC_DE_OFFSET]`
- [./rt102x/README.md](./rt102x/README.md)
- [./rt105x/README.md](./rt105x/README.md)
- [./rt106x/README.md](./rt106x/README.md)
- [./rt117x/README.md](./rt117x/README.md)
- [./rt118x/README.md](./rt118x/README.md)

## Invariants
- `[imxrt_ccm.h:#error]` Compile-time guard: Unrecognized i.MX RT architecture
- `[imxrt_dmamux.h:#error]` Compile-time guard: Unrecognized i.MX RT architecture
- `[imxrt_gpio.h:#error]` Compile-time guard: Unrecognized i.MX RT architecture
- `[imxrt_iomuxc_ver1.h:#error]` Compile-time guard: Unrecognized i.MX RT architecture
- `[imxrt_iomuxc_ver2.h:#error]` Compile-time guard: Unrecognized i.MX RT architecture
- `[imxrt_memorymap.h:#error]` Compile-time guard: Unrecognized i.MX RT architecture
- `[imxrt_pinmux.h:#error]` Compile-time guard: Unrecognized i.MX RT architecture
- `[imxrt_xbar.h:#error]` Compile-time guard: Unrecognized i.MX RT architecture

## Side Effects
- None

## Verification
- Run: `make test`
