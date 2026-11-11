# imx93 (`nuttx/arch/arm/src/imx9/hardware/imx93`)

## Overview
Hardware abstraction and architecture package for `imx93` under `nuttx/arch/arm/src/imx9/hardware/imx93`, providing 9 header file(s) and 0 source file(s) (including `imx93_ccm.h`, `imx93_clock.h`, `imx93_dmamux.h`, `imx93_edma.h`).

## Interface
- `[imx93_ccm.h:ccm_clock_name_e]`
- `[imx93_ccm.h:IMX9_CCM_CR_CTRL_OFFSET]`
- `[imx93_ccm.h:IMX9_CCM_CR_CTRL_SET_OFFSET]`
- `[imx93_ccm.h:IMX9_CCM_CR_CTRL_CLR_OFFSET]`
- `[imx93_ccm.h:IMX9_CCM_CR_CTRL_TOG_OFFSET]`
- `[imx93_ccm.h:IMX9_CCM_CR_STAT0_OFFSET]`
- `[imx93_ccm.h:IMX9_CCM_CR_AUTH_OFFSET]`
- `[imx93_ccm.h:IMX9_CCM_CR_AUTH_SET_OFFSET]`
- `[imx93_ccm.h:IMX9_CCM_CR_AUTH_CLR_OFFSET]`
- `[imx93_ccm.h:IMX9_CCM_CR_AUTH_TOG_OFFSET]`
- `[imx93_ccm.h:IMX9_CCM_GPR_SH_OFFSET]`
- `[imx93_ccm.h:IMX9_CCM_GPR_SH_SET_OFFSET]`
- `[imx93_ccm.h:IMX9_CCM_GPR_SH_CLR_OFFSET]`
- `[imx93_clock.h:clock_config_t]`
- `[imx93_clock.h:XTAL_FREQ]`
- `[imx93_clock.h:CLOCK_GATE_SHIFT]`
- `[imx93_clock.h:CLOCK_GATE_MASK]`
- `[imx93_clock.h:CLOCK_GATE]`
- `[imx93_clock.h:GET_CLOCK_GATE]`
- `[imx93_clock.h:CLOCK_DIV_SHIFT]`
- `[imx93_clock.h:CLOCK_DIV_MASK]`
- `[imx93_clock.h:CLOCK_DIV]`
- `[imx93_clock.h:GET_CLOCK_DIV]`
- `[imx93_clock.h:CLOCK_ROOT_SHIFT]`
- `[imx93_clock.h:CLOCK_ROOT_MASK]`
- `[imx93_clock.h:CLOCK_ROOT]`
- `[imx93_dmamux.h:EDMA3_MUX_ID]`
- `[imx93_dmamux.h:EDMA4_MUX_ID]`
- `[imx93_dmamux.h:EDMA_MUX_ID_MASK]`
- `[imx93_dmamux.h:EDMA_MUX_MASK]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
