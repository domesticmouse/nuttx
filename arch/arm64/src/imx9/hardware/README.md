# hardware (`nuttx/arch/arm64/src/imx9/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm64/src/imx9/hardware`, providing 23 header file(s) and 0 source file(s) (including `imx9_blk_ctrl.h`, `imx9_ccm.h`, `imx9_dmamux.h`, `imx9_edma.h`).

## Subdirectories & Boundaries
- `imx93`: [./imx93/README.md](./imx93/README.md) - Hardware abstraction and architecture package for `imx93` under `nuttx/arch/arm64/src/imx9/hardware/imx93`, providing 8 header file(s) and 0 source file(s) (including `imx93_ccm.h`, `imx93_dmamux.h`, `imx93_edma.h`, `imx93_gpio.h`).
- `imx95`: [./imx95/README.md](./imx95/README.md) - Hardware abstraction and architecture package for `imx95` under `nuttx/arch/arm64/src/imx9/hardware/imx95`, providing 7 header file(s) and 0 source file(s) (including `imx95_ccm.h`, `imx95_clock.h`, `imx95_gpio.h`, `imx95_iomuxc.h`).

## Interface
- `[imx9_blk_ctrl.h:IMX9_WAKUPMIX_IPG_DEBUG_CM33_OFFSET]`
- `[imx9_blk_ctrl.h:IMX9_WAKUPMIX_QCH_DIS_OFFSET]`
- `[imx9_blk_ctrl.h:IMX9_WAKUPMIX_DEXSC_ERR_OFFSET]`
- `[imx9_blk_ctrl.h:IMX9_WAKUPMIX_MQS_SETTING_OFFSET]`
- `[imx9_blk_ctrl.h:IMX9_WAKUPMIX_SAI_CLK_SEL_OFFSET]`
- `[imx9_blk_ctrl.h:IMX9_WAKUPMIX_GPR_OFFSET]`
- `[imx9_blk_ctrl.h:IMX9_WAKUPMIX_ENET_CLK_SEL_OFFSET]`
- `[imx9_blk_ctrl.h:IMX9_WAKUPMIX_VOLT_DETECT_OFFSET]`
- `[imx9_blk_ctrl.h:IMX9_WAKUPMIX_I3C2_WAKEUP_OFFSET]`
- `[imx9_blk_ctrl.h:IMX9_WAKUPMIX_IPG_DEBUG_CA55C0_OFFSET]`
- `[imx9_blk_ctrl.h:IMX9_WAKUPMIX_IPG_DEBUG_CA55C1_OFFSET]`
- `[imx9_blk_ctrl.h:IMX9_WAKUPMIX_AXI_ATTR_CFG_OFFSET]`
- `[imx9_ele.h:ele_header_t]`
- `[imx9_ele.h:ele_msg]`
- `[imx9_ele.h:ELE_MAX_MSG]`
- `[imx9_ele.h:ELE_CMD_TAG]`
- `[imx9_ele.h:ELE_VERSION]`
- `[imx9_ele.h:ELE_VERSION_FW]`
- `[imx9_ele.h:ELE_RESP_TAG]`
- `[imx9_ele.h:ELE_OK]`
- `[imx9_ele.h:ELE_DERIVE_KEY_REQ]`
- `[imx9_ele.h:ELE_GET_EVENTS_REQ]`
- `[imx9_ele.h:ELE_GET_TRNG_STATE_REQ]`
- `[imx9_ele.h:ELE_GET_RNG_REQ]`
- `[imx9_ele.h:ELE_FWD_LIFECYCLE_UP_REQ]`
- `[imx9_ele.h:ELE_OEM_CNTN_AUTH_REQ]`
- `[imx9_enet.h:enet_desc_s]`
- `[imx9_enet.h:enet_txdesc_s]`
- `[imx9_enet.h:IMX9_ENET_EIR_OFFSET]`
- `[imx9_enet.h:IMX9_ENET_EIMR_OFFSET]`
- [./imx93/README.md](./imx93/README.md)
- [./imx95/README.md](./imx95/README.md)

## Invariants
- `[imx9_ccm.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_dmamux.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_edma.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_gpio.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_memorymap.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_pinmux.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture

## Side Effects
- None

## Verification
- Run: `make test`
