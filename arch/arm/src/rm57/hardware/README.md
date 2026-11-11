# hardware (`nuttx/arch/arm/src/rm57/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/rm57/hardware`, providing 23 header file(s) and 0 source file(s) (including `rm57_adc.h`, `rm57_ccm.h`, `rm57_dcan.h`, `rm57_dma.h`).

## Interface
- `[rm57_adc.h:RM57_ADC_RSTCR_OFFSET]`
- `[rm57_adc.h:RM57_ADC_OPMODECR_OFFSET]`
- `[rm57_adc.h:RM57_ADC_CLOCKCR_OFFSET]`
- `[rm57_adc.h:RM57_ADC_CALCR_OFFSET]`
- `[rm57_adc.h:RM57_ADC_EVMODECR_OFFSET]`
- `[rm57_adc.h:RM57_ADC_G1MODECR_OFFSET]`
- `[rm57_adc.h:RM57_ADC_G2MODECR_OFFSET]`
- `[rm57_adc.h:RM57_ADC_EVSRC_OFFSET]`
- `[rm57_adc.h:RM57_ADC_G1SRC_OFFSET]`
- `[rm57_adc.h:RM57_ADC_G2SRC_OFFSET]`
- `[rm57_adc.h:RM57_ADC_EVINTENA_OFFSET]`
- `[rm57_adc.h:RM57_ADC_G1INTENA_OFFSET]`
- `[rm57_ccm.h:RM57_CCM_SR1_OFFSET]`
- `[rm57_ccm.h:RM57_CCM_KEYR1_OFFSET]`
- `[rm57_ccm.h:RM57_CCM_SR2_OFFSET]`
- `[rm57_ccm.h:RM57_CCM_KEYR2_OFFSET]`
- `[rm57_ccm.h:RM57_CCM_SR3_OFFSET]`
- `[rm57_ccm.h:RM57_CCM_KEYR3_OFFSET]`
- `[rm57_ccm.h:RM57_CCM_POLCNTRL_OFFSET]`
- `[rm57_ccm.h:RM57_CCM_SR4_OFFSET]`
- `[rm57_ccm.h:RM57_CCM_KEYR4_OFFSET]`
- `[rm57_ccm.h:RM57_CCM_PDSTAT0_OFFSET]`
- `[rm57_ccm.h:RM57_CCM_SR1]`
- `[rm57_ccm.h:RM57_CCM_KEYR1]`
- `[rm57_dcan.h:RM57_DCAN_NMSGOBJ]`
- `[rm57_dcan.h:RM57_DCAN_RAM_MBOX]`
- `[rm57_dcan.h:RM57_DCAN_RAM_ECC]`
- `[rm57_dcan.h:RM57_DCAN_CTL_OFFSET]`
- `[rm57_dcan.h:RM57_DCAN_ES_OFFSET]`
- `[rm57_dcan.h:RM57_DCAN_ERRC_OFFSET]`

## Invariants
- `[rm57_pinmux.h:#error]` Compile-time guard: Unrecognized RM57 chip

## Side Effects
- None

## Verification
- Run: `make test`
