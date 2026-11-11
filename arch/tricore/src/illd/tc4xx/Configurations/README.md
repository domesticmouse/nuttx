# Configurations (`nuttx/arch/tricore/src/illd/tc4xx/Configurations`)

## Overview
Hardware abstraction and architecture package for `Configurations` under `nuttx/arch/tricore/src/illd/tc4xx/Configurations`, providing 2 header file(s) and 1 source file(s) (including `Ifx_Cfg.h`, `Ifx_Cfg_Ssw.h`, `Ifx_Cfg_Ssw.c`).

## Interface
- `[Ifx_Cfg.h:DEVICE_TC4DX]`
- `[Ifx_Cfg.h:IFX_CFG_CLOCK_XTAL_FREQUENCY]`
- `[Ifx_Cfg.h:IFX_CFG_CLOCK_SYSPLL_FREQUENCY]`
- `[Ifx_Cfg.h:IFX_CFG_CLOCK_PPUPLL_FREQUENCY]`
- `[Ifx_Cfg.h:IFX_CFG_CLOCK_PERPLL1_FREQUENCY]`
- `[Ifx_Cfg.h:IFX_CFG_CLOCK_PERPLL2_FREQUENCY]`
- `[Ifx_Cfg.h:IFX_CFG_CLOCK_PERPLL3_FREQUENCY]`
- `[Ifx_Cfg.h:IFX_CFG_CPU_CLOCK_FREQUENCY]`
- `[Ifx_Cfg.h:IFX_PROT_ENABLED]`
- `[Ifx_Cfg.h:IFX_CFG_VIRTUALIZATION_DISABLED]`
- `[Ifx_Cfg.h:IFX_CFG_STM_MORPHING_ENABLE]`
- `[Ifx_Cfg.h:IFX_CLOCK_BYPASS_FOSC_F]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_LBIST]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_MONBIST]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_MBIST_DSPRS_DMARAM]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_XTALSRC_CHECK]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_PLL_INIT]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_MBIST]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_SMU]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_AP_INIT]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_KEYOFF_LBIST]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_KEYOFF_MBIST]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_KEYOFF_MBIST_DSPRS_DMARAM]`
- `[Ifx_Cfg_Ssw.c:Ifx_Ssw_Lbist]`
- `[Ifx_Cfg_Ssw.c:Ifx_Ssw_Monbist]`
- `[Ifx_Cfg_Ssw.c:Ifx_Ssw_MbistDsprsDmaRam]`
- `[Ifx_Cfg_Ssw.c:Ifx_Ssw_PowerOnCrystalOsc]`
- `[Ifx_Cfg_Ssw.c:Ifx_Ssw_PllInit]`
- `[Ifx_Cfg_Ssw.c:Ifx_Ssw_Mbist]`
- `[Ifx_Cfg_Ssw.c:Ifx_Ssw_Smu]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
