# rm57 (`nuttx/arch/arm/include/rm57`)

## Overview
Hardware abstraction and architecture package for `rm57` under `nuttx/arch/arm/include/rm57`, providing 4 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `rm57_adc_ioctl.h`, `rm57l843_irq.h`).

## Interface
- `[chip.h:RM57_CORTEX_R5F]`
- `[chip.h:RM57_PFLASH]`
- `[chip.h:RM57_SRAM]`
- `[chip.h:RM57_NCAN]`
- `[chip.h:RM57_NSCI]`
- `[chip.h:RM57_NMIBSPI]`
- `[chip.h:RM57_NGIOPORT]`
- `[irq.h:RM57_VECT_PHANTOM]`
- `[irq.h:NR_IRQS]`
- `[rm57_adc_ioctl.h:rm57_adc_grpcfg_s]`
- `[rm57_adc_ioctl.h:rm57_adc_calib_s]`
- `[rm57_adc_ioctl.h:rm57_adc_selftest_s]`
- `[rm57_adc_ioctl.h:rm57_adc_magcomp_s]`
- `[rm57_adc_ioctl.h:rm57_adc_chnseq_s]`
- `[rm57_adc_ioctl.h:rm57_adc_temp_s]`
- `[rm57_adc_ioctl.h:rm57_adc_evtpin_s]`
- `[rm57_adc_ioctl.h:RM57_ADC_MODULE1]`
- `[rm57_adc_ioctl.h:RM57_ADC_MODULE2]`
- `[rm57_adc_ioctl.h:RM57_ADC_NMODULES]`
- `[rm57_adc_ioctl.h:RM57_ADC_GROUP_EV]`
- `[rm57_adc_ioctl.h:RM57_ADC_GROUP_G1]`
- `[rm57_adc_ioctl.h:RM57_ADC_GROUP_G2]`
- `[rm57_adc_ioctl.h:RM57_ADC_NGROUPS]`
- `[rm57_adc_ioctl.h:RM57_ADC_NMAGCOMP]`
- `[rm57_adc_ioctl.h:RM57_ADC_LUT_NENTRIES]`
- `[rm57_adc_ioctl.h:RM57_ADC_NTEMPSENSORS]`
- `[rm57_adc_ioctl.h:RM57_ADC_TEMPCAL_NPOINTS]`
- `[rm57_adc_ioctl.h:ADC_TRIGSRC_EVT]`
- `[rm57l843_irq.h:RM57_IRQ_NCHANNELS]`
- `[rm57l843_irq.h:RM57_REQ_ESMHIGH]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unrecognized RM57 chip
- `[irq.h:#error]` Compile-time guard: Unrecognized Hercules RM57 chip

## Side Effects
- None

## Verification
- Run: `make test`
