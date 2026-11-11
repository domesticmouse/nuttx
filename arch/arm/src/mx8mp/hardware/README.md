# hardware (`nuttx/arch/arm/src/mx8mp/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/mx8mp/hardware`, providing 10 header file(s) and 0 source file(s) (including `mx8mp_ccm.h`, `mx8mp_ecspi.h`, `mx8mp_gpc.h`, `mx8mp_gpio.h`).

## Interface
- `[mx8mp_ccm.h:CCM_GPR0]`
- `[mx8mp_ccm.h:CCM_PLL_BASE]`
- `[mx8mp_ccm.h:CCM_CCGR_BASE]`
- `[mx8mp_ccm.h:CCM_CLK_ROOT_BASE]`
- `[mx8mp_ccm.h:CCM_SET]`
- `[mx8mp_ccm.h:CCM_CLR]`
- `[mx8mp_ccm.h:CCM_TOG]`
- `[mx8mp_ccm.h:CCM_DVFS_CLK_GATE]`
- `[mx8mp_ccm.h:CCM_ANAMIX_CLK_GATE]`
- `[mx8mp_ccm.h:CCM_CPU_CLK_GATE]`
- `[mx8mp_ccm.h:CCM_CSU_CLK_GATE]`
- `[mx8mp_ccm.h:CCM_DEBUG_CLK_GATE]`
- `[mx8mp_ecspi.h:RXDATA_OFFSET]`
- `[mx8mp_ecspi.h:TXDATA_OFFSET]`
- `[mx8mp_ecspi.h:CONREG_OFFSET]`
- `[mx8mp_ecspi.h:CONFIGREG_OFFSET]`
- `[mx8mp_ecspi.h:INTREG_OFFSET]`
- `[mx8mp_ecspi.h:DMAREG_OFFSET]`
- `[mx8mp_ecspi.h:STATREG_OFFSET]`
- `[mx8mp_ecspi.h:PERIODREG_OFFSET]`
- `[mx8mp_ecspi.h:TESTREG_OFFSET]`
- `[mx8mp_ecspi.h:MSGDATA_OFFSET]`
- `[mx8mp_ecspi.h:CONREG_BURST_LENGTH]`
- `[mx8mp_ecspi.h:CONREG_CHANNEL_SELECT]`
- `[mx8mp_gpc.h:GPC_PU_PGC_SW_PUP_REQ]`
- `[mx8mp_gpc.h:GPC_PGC_CPU_M7_MAPPING]`
- `[mx8mp_gpc.h:GPC_PU_PWRHSK]`
- `[mx8mp_gpc.h:AUDIOMIX_DOMAIN]`
- `[mx8mp_gpc.h:AUDIOMIX_SW_PUP_REQ]`
- `[mx8mp_gpc.h:GPC_AUDIOMIX_NOC_PWRDNREQN]`

## Invariants
- None

## Side Effects
- `[mx8mp_rdc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers

## Verification
- Run: `make test`
