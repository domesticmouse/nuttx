# hardware (`nuttx/arch/arm/src/imx6/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/imx6/hardware`, providing 10 header file(s) and 0 source file(s) (including `imx_ccm.h`, `imx_ecspi.h`, `imx_enet.h`, `imx_gpio.h`).

## Interface
- `[imx_ccm.h:IMX_CCM_CCR_OFFSET]`
- `[imx_ccm.h:IMX_CCM_CCDR_OFFSET]`
- `[imx_ccm.h:IMX_CCM_CSR_OFFSET]`
- `[imx_ccm.h:IMX_CCM_CCSR_OFFSET]`
- `[imx_ccm.h:IMX_CCM_CACRR_OFFSET]`
- `[imx_ccm.h:IMX_CCM_CBCDR_OFFSET]`
- `[imx_ccm.h:IMX_CCM_CBCMR_OFFSET]`
- `[imx_ccm.h:IMX_CCM_CSCMR1_OFFSET]`
- `[imx_ccm.h:IMX_CCM_CSCMR2_OFFSET]`
- `[imx_ccm.h:IMX_CCM_CSCDR1_OFFSET]`
- `[imx_ccm.h:IMX_CCM_CS1CDR_OFFSET]`
- `[imx_ccm.h:IMX_CCM_CS2CDR_OFFSET]`
- `[imx_ecspi.h:ECSPI_RXDATA_OFFSET]`
- `[imx_ecspi.h:ECSPI_TXDATA_OFFSET]`
- `[imx_ecspi.h:ECSPI_CONREG_OFFSET]`
- `[imx_ecspi.h:ECSPI_CONFIGREG_OFFSET]`
- `[imx_ecspi.h:ECSPI_INTREG_OFFSET]`
- `[imx_ecspi.h:ECSPI_DMAREG_OFFSET]`
- `[imx_ecspi.h:ECSPI_STATREG_OFFSET]`
- `[imx_ecspi.h:ECSPI_PERIODREG_OFFSET]`
- `[imx_ecspi.h:ECSPI_TESTREG_OFFSET]`
- `[imx_ecspi.h:ECSPI_MSGDATA_OFFSET]`
- `[imx_ecspi.h:IMX_ECSPI1_RXDATA]`
- `[imx_ecspi.h:IMX_ECSPI1_TXDATA]`
- `[imx_enet.h:enet_desc_s]`
- `[imx_enet.h:IMX_ENET_HAS_DBSWAP]`
- `[imx_enet.h:IMX_ENET_EIR_OFFSET]`
- `[imx_enet.h:IMX_ENET_EIMR_OFFSET]`
- `[imx_enet.h:IMX_ENET_RDAR_OFFSET]`
- `[imx_enet.h:IMX_ENET_TDAR_OFFSET]`

## Invariants
- `[imx_memorymap.h:#error]` Compile-time guard: EIM FLASH size disagreement

## Side Effects
- None

## Verification
- Run: `make test`
