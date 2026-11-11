# hardware (`nuttx/arch/risc-v/src/bl602/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/bl602/hardware`, providing 22 header file(s) and 0 source file(s) (including `bl602_aon.h`, `bl602_cci.h`, `bl602_cks.h`, `bl602_clic.h`).

## Interface
- `[bl602_aon.h:BL602_AON_OFFSET]`
- `[bl602_aon.h:BL602_AON_COMMON_OFFSET]`
- `[bl602_aon.h:BL602_AON_MISC_OFFSET]`
- `[bl602_aon.h:BL602_BG_SYS_TOP_OFFSET]`
- `[bl602_aon.h:BL602_DCDC18_TOP_0_OFFSET]`
- `[bl602_aon.h:BL602_DCDC18_TOP_1_OFFSET]`
- `[bl602_aon.h:BL602_LDO11SOC_AND_DCTEST_OFFSET]`
- `[bl602_aon.h:BL602_PSW_IRRCV_OFFSET]`
- `[bl602_aon.h:BL602_RF_TOP_AON_OFFSET]`
- `[bl602_aon.h:BL602_XTAL_CFG_OFFSET]`
- `[bl602_aon.h:BL602_TSEN_OFFSET]`
- `[bl602_aon.h:BL602_ACOMP0_CTRL_OFFSET]`
- `[bl602_cci.h:BL602_CCI_CFG_OFFSET]`
- `[bl602_cci.h:BL602_CCI_ADDR_OFFSET]`
- `[bl602_cci.h:BL602_CCI_WDATA_OFFSET]`
- `[bl602_cci.h:BL602_CCI_RDATA_OFFSET]`
- `[bl602_cci.h:BL602_CCI_CTL_OFFSET]`
- `[bl602_cci.h:BL602_CCI_CFG]`
- `[bl602_cci.h:BL602_CCI_ADDR]`
- `[bl602_cci.h:BL602_CCI_WDATA]`
- `[bl602_cci.h:BL602_CCI_RDATA]`
- `[bl602_cci.h:BL602_CCI_CTL]`
- `[bl602_cci.h:CCI_CFG_REG_MCCI_CLK_INV]`
- `[bl602_cci.h:CCI_CFG_REG_SCCI_CLK_INV]`
- `[bl602_cks.h:BL602_CKS_CONFIG_OFFSET]`
- `[bl602_cks.h:BL602_CKS_DATA_IN_OFFSET]`
- `[bl602_cks.h:BL602_CKS_OUT_OFFSET]`
- `[bl602_cks.h:BL602_CKS_CONFIG]`
- `[bl602_cks.h:BL602_CKS_DATA_IN]`
- `[bl602_cks.h:BL602_CKS_OUT]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
