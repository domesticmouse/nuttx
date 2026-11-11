# Configurations (`nuttx/arch/tricore/src/illd/tc3xx/Configurations`)

## Overview
Hardware abstraction and architecture package for `Configurations` under `nuttx/arch/tricore/src/illd/tc3xx/Configurations`, providing 2 header file(s) and 1 source file(s) (including `Ifx_Cfg.h`, `Ifx_Cfg_Ssw.h`, `Ifx_Cfg_Ssw.c`).

## Interface
- `[Ifx_Cfg.h:DEVICE_TC39XB]`
- `[Ifx_Cfg.h:IFX_PIN_PACKAGE_LFBGA292]`
- `[Ifx_Cfg.h:IFX_CFG_SCU_XTAL_FREQUENCY]`
- `[Ifx_Cfg.h:IFX_CFG_SCU_PLL_FREQUENCY]`
- `[Ifx_Cfg.h:IFX_CFG_SCU_PLL1_FREQUENCY]`
- `[Ifx_Cfg.h:IFX_CFG_SCU_PLL2_FREQUENCY]`
- `[Ifx_Cfg.h:IFX_CFG_CPU_CLOCK_FREQUENCY]`
- `[Ifx_Cfg.h:ISR_PRIORITY_STM_TICK]`
- `[Ifx_Cfg.h:ISR_PRIORITY_GETH_DMA0_TX]`
- `[Ifx_Cfg.h:ISR_PRIORITY_GETH_DMA0_RX]`
- `[Ifx_Cfg.h:IFX_CFG_SSW_ENABLE_TRICORE0]`
- `[Ifx_Cfg.h:IFX_CFG_SSW_ENABLE_TRICORE1]`
- `[Ifx_Cfg_Ssw.h:Ifx_Ssw_Lbist]`
- `[Ifx_Cfg_Ssw.h:Ifx_Ssw_Monbist]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_LBIST]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_MONBIST]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_PLL_INIT]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_MBIST]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_SMU]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_ENABLE_EMEM_INIT]`
- `[Ifx_Cfg_Ssw.h:IFX_SCU_FLASHWAITSTATECHECK]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_CALLOUT_LBIST]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_CALLOUT_MONBIST]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_CALLOUT_PLL_INIT]`
- `[Ifx_Cfg_Ssw.h:IFX_CFG_SSW_CALLOUT_MBIST]`
- `[Ifx_Cfg_Ssw.c:Ifx_Ssw_Lbist]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
