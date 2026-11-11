# imx93 (`nuttx/arch/arm64/src/imx9/hardware/imx93`)

## Overview
Hardware abstraction and architecture package for `imx93` under `nuttx/arch/arm64/src/imx9/hardware/imx93`, providing 8 header file(s) and 0 source file(s) (including `imx93_ccm.h`, `imx93_dmamux.h`, `imx93_edma.h`, `imx93_gpio.h`).

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
- `[imx93_dmamux.h:EDMA3_MUX_ID]`
- `[imx93_dmamux.h:EDMA4_MUX_ID]`
- `[imx93_dmamux.h:EDMA_MUX_ID_MASK]`
- `[imx93_dmamux.h:EDMA_MUX_MASK]`
- `[imx93_dmamux.h:DMA_REQUEST_DISABLED]`
- `[imx93_dmamux.h:DMA_REQUEST_MUXCAN1]`
- `[imx93_dmamux.h:DMA_REQUEST_MUXGPIO1_0]`
- `[imx93_dmamux.h:DMA_REQUEST_MUXGPIO1_1]`
- `[imx93_dmamux.h:DMA_REQUEST_MUXI3C1TOBUS]`
- `[imx93_dmamux.h:DMA_REQUEST_MUXI3C1FROMBUS]`
- `[imx93_dmamux.h:DMA_REQUEST_MUXLPI2C1TX]`
- `[imx93_dmamux.h:DMA_REQUEST_MUXLPI2C1RX]`
- `[imx93_edma.h:imx9_edmatcd_s]`
- `[imx93_edma.h:IMX9_EDMA_CSR_OFFSET]`
- `[imx93_edma.h:IMX9_EDMA_ES_OFFSET]`
- `[imx93_edma.h:IMX9_EDMA_CH_GRPRI_OFFSET]`
- `[imx93_edma.h:IMX9_EDMA_INT_OFFSET]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
