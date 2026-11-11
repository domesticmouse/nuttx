# hardware (`nuttx/arch/arm/src/kinetis/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/kinetis/hardware`, providing 65 header file(s) and 0 source file(s) (including `kinetis_adc.h`, `kinetis_aips.h`, `kinetis_axbs.h`, `kinetis_cmp.h`).

## Interface
- `[kinetis_adc.h:KINETIS_ADC_SC1A_OFFSET]`
- `[kinetis_adc.h:KINETIS_ADC_SC1B_OFFSET]`
- `[kinetis_adc.h:KINETIS_ADC_CFG1_OFFSET]`
- `[kinetis_adc.h:KINETIS_ADC_CFG2_OFFSET]`
- `[kinetis_adc.h:KINETIS_ADC_RA_OFFSET]`
- `[kinetis_adc.h:KINETIS_ADC_RB_OFFSET]`
- `[kinetis_adc.h:KINETIS_ADC_CV1_OFFSET]`
- `[kinetis_adc.h:KINETIS_ADC_CV2_OFFSET]`
- `[kinetis_adc.h:KINETIS_ADC_SC2_OFFSET]`
- `[kinetis_adc.h:KINETIS_ADC_SC3_OFFSET]`
- `[kinetis_adc.h:KINETIS_ADC_OFS_OFFSET]`
- `[kinetis_adc.h:KINETIS_ADC_PG_OFFSET]`
- `[kinetis_aips.h:KINETIS_AIPS_MPRA_OFFSET]`
- `[kinetis_aips.h:KINETIS_AIPS_PACRA_OFFSET]`
- `[kinetis_aips.h:KINETIS_AIPS_PACRB_OFFSET]`
- `[kinetis_aips.h:KINETIS_AIPS_PACRC_OFFSET]`
- `[kinetis_aips.h:KINETIS_AIPS_PACRD_OFFSET]`
- `[kinetis_aips.h:KINETIS_AIPS_PACRE_OFFSET]`
- `[kinetis_aips.h:KINETIS_AIPS_PACRF_OFFSET]`
- `[kinetis_aips.h:KINETIS_AIPS_PACRG_OFFSET]`
- `[kinetis_aips.h:KINETIS_AIPS_PACRH_OFFSET]`
- `[kinetis_aips.h:KINETIS_AIPS_PACRI_OFFSET]`
- `[kinetis_aips.h:KINETIS_AIPS_PACRJ_OFFSET]`
- `[kinetis_aips.h:KINETIS_AIPS_PACRK_OFFSET]`
- `[kinetis_axbs.h:KINETIS_AXBS_PRS_OFFSET]`
- `[kinetis_axbs.h:KINETIS_AXBS_CRS_OFFSET]`
- `[kinetis_axbs.h:KINETIS_AXBS_MGPCR_OFFSET]`
- `[kinetis_axbs.h:KINETIS_AXBS_PRS0_OFFSET]`
- `[kinetis_axbs.h:KINETIS_AXBS_CRS0_OFFSET]`
- `[kinetis_axbs.h:KINETIS_AXBS_PRS1_OFFSET]`

## Invariants
- `[kinetis_fmc.h:#error]` Compile-time guard: No FMC definitions for this Kinetis part
- `[kinetis_k20pinmux.h:#error]` Compile-time guard: No pin multiplexing for this Kinetis K20 part
- `[kinetis_k28memorymap.h:#error]` Compile-time guard: No memory map for this K28 part
- `[kinetis_k40pinmux.h:#error]` Compile-time guard: No pin multiplexing for this Kinetis K40 part
- `[kinetis_k60pinmux.h:#error]` Compile-time guard: No pin multiplexing for this Kinetis K60 part
- `[kinetis_k64memorymap.h:#error]` Compile-time guard: No memory map for this K64 part
- `[kinetis_k66memorymap.h:#error]` Compile-time guard: No memory map for this K66 part
- `[kinetis_memorymap.h:#error]` Compile-time guard: No memory map for this Kinetis part
- `[kinetis_mpu.h:#error]` Compile-time guard: No MPU definitions for this Kinetis part
- `[kinetis_pinmux.h:#error]` Compile-time guard: No pin multiplexing for this Kinetis part

## Side Effects
- None

## Verification
- Run: `make test`
