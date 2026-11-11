# hardware (`nuttx/arch/arm/src/xmc4/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/xmc4/hardware`, providing 12 header file(s) and 0 source file(s) (including `xmc4_ccu4.h`, `xmc4_eru.h`, `xmc4_eru_pinmap.h`, `xmc4_ethernet.h`).

## Interface
- `[xmc4_ccu4.h:XMC4_CCU4_GCTRL_OFFSET]`
- `[xmc4_ccu4.h:XMC4_CCU4_GSTAT_OFFSET]`
- `[xmc4_ccu4.h:XMC4_CCU4_GIDLS_OFFSET]`
- `[xmc4_ccu4.h:XMC4_CCU4_GIDLC_OFFSET]`
- `[xmc4_ccu4.h:XMC4_CCU4_GCSS_OFFSET]`
- `[xmc4_ccu4.h:XMC4_CCU4_GCSC_OFFSET]`
- `[xmc4_ccu4.h:XMC4_CCU4_GCST_OFFSET]`
- `[xmc4_ccu4.h:XMC4_CCU4_MIDR_OFFSET]`
- `[xmc4_ccu4.h:XMC4_CCU4_CC40INS_OFFSET]`
- `[xmc4_ccu4.h:XMC4_CCU4_CC40CMC_OFFSET]`
- `[xmc4_ccu4.h:XMC4_CCU4_CC40TST_OFFSET]`
- `[xmc4_ccu4.h:XMC4_CCU4_CC40TCSET_OFFSET]`
- `[xmc4_eru.h:XMC4_ERU_EXISEL_OFFSET]`
- `[xmc4_eru.h:XMC4_ERU_EXICON0_OFFSET]`
- `[xmc4_eru.h:XMC4_ERU_EXICON1_OFFSET]`
- `[xmc4_eru.h:XMC4_ERU_EXICON2_OFFSET]`
- `[xmc4_eru.h:XMC4_ERU_EXICON3_OFFSET]`
- `[xmc4_eru.h:XMC4_ERU_EXOCON0_OFFSET]`
- `[xmc4_eru.h:XMC4_ERU_EXOCON1_OFFSET]`
- `[xmc4_eru.h:XMC4_ERU_EXOCON2_OFFSET]`
- `[xmc4_eru.h:XMC4_ERU_EXOCON3_OFFSET]`
- `[xmc4_eru.h:XMC4_ERU0_EXISEL]`
- `[xmc4_eru.h:XMC4_ERU0_EXICON0]`
- `[xmc4_eru.h:XMC4_ERU0_EXICON1]`
- `[xmc4_eru_pinmap.h:ERU0_ETL0_INPUTA_P0_1]`
- `[xmc4_eru_pinmap.h:ERU0_ETL0_INPUTA_P2_5]`
- `[xmc4_eru_pinmap.h:ERU0_ETL0_INPUTA_P3_2]`
- `[xmc4_eru_pinmap.h:ERU0_ETL0_INPUTB_P0_0]`
- `[xmc4_eru_pinmap.h:ERU0_ETL0_INPUTB_P2_0]`
- `[xmc4_eru_pinmap.h:ERU0_ETL0_INPUTB_P2_4]`

## Invariants
- `[xmc4_vadc.h:#error]` Compile-time guard: Unsupported XMC4xxx chip

## Side Effects
- None

## Verification
- Run: `make test`
