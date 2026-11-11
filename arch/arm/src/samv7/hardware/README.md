# hardware (`nuttx/arch/arm/src/samv7/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/samv7/hardware`, providing 34 header file(s) and 0 source file(s) (including `sam_afec.h`, `sam_chipid.h`, `sam_dacc.h`, `sam_eefc.h`).

## Interface
- `[sam_afec.h:SAM_ADC_NCHANNELS]`
- `[sam_afec.h:SAM_AFEC_CR_OFFSET]`
- `[sam_afec.h:SAM_AFEC_MR_OFFSET]`
- `[sam_afec.h:SAM_AFEC_EMR_OFFSET]`
- `[sam_afec.h:SAM_AFEC_SEQ1R_OFFSET]`
- `[sam_afec.h:SAM_AFEC_SEQ2R_OFFSET]`
- `[sam_afec.h:SAM_AFEC_CHER_OFFSET]`
- `[sam_afec.h:SAM_AFEC_CHDR_OFFSET]`
- `[sam_afec.h:SAM_AFEC_CHSR_OFFSET]`
- `[sam_afec.h:SAM_AFEC_LCDR_OFFSET]`
- `[sam_afec.h:SAM_AFEC_IER_OFFSET]`
- `[sam_afec.h:SAM_AFEC_IDR_OFFSET]`
- `[sam_chipid.h:SAM_CHIPID_CIDR_OFFSET]`
- `[sam_chipid.h:SAM_CHIPID_EXID_OFFSET]`
- `[sam_chipid.h:SAM_CHIPID_CIDR]`
- `[sam_chipid.h:SAM_CHIPID_EXID]`
- `[sam_chipid.h:CHIPID_CIDR_VERSION_SHIFT]`
- `[sam_chipid.h:CHIPID_CIDR_VERSION_MASK]`
- `[sam_chipid.h:CHIPID_CIDR_EPROC_SHIFT]`
- `[sam_chipid.h:CHIPID_CIDR_EPROC_MASK]`
- `[sam_chipid.h:CHIPID_CIDR_EPROC_CORTEXM7]`
- `[sam_chipid.h:CHIPID_CIDR_EPROC_ARM946ES]`
- `[sam_chipid.h:CHIPID_CIDR_EPROC_ARM7TDMI]`
- `[sam_chipid.h:CHIPID_CIDR_EPROC_CORTEXM3]`
- `[sam_dacc.h:SAM_DACC_CR_OFFSET]`
- `[sam_dacc.h:SAM_DACC_MR_OFFSET]`
- `[sam_dacc.h:SAM_DACC_TRIGR_OFFSET]`
- `[sam_dacc.h:SAM_DACC_CHER_OFFSET]`
- `[sam_dacc.h:SAM_DACC_CHDR_OFFSET]`
- `[sam_dacc.h:SAM_DACC_CHSR_OFFSET]`

## Invariants
- `[sam_memorymap.h:#error]` Compile-time guard: Unrecognized SAMV7 architecture
- `[sam_pinmap.h:#error]` Compile-time guard: Unrecognized SAMV7 architecture

## Side Effects
- None

## Verification
- Run: `make test`
