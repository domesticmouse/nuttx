# hardware (`nuttx/arch/arm64/src/zynq-mpsoc/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm64/src/zynq-mpsoc/hardware`, providing 3 header file(s) and 0 source file(s) (including `zynq_gmac.h`, `zynq_memorymap.h`, `zynq_pll.h`).

## Interface
- `[zynq_gmac.h:gmac_rxdesc_s]`
- `[zynq_gmac.h:gmac_txdesc_s]`
- `[zynq_gmac.h:ZYNQ_GMAC_NCR]`
- `[zynq_gmac.h:ZYNQ_GMAC_NCFGR]`
- `[zynq_gmac.h:ZYNQ_GMAC_NSR]`
- `[zynq_gmac.h:ZYNQ_GMAC_UR]`
- `[zynq_gmac.h:ZYNQ_GMAC_DCFGR]`
- `[zynq_gmac.h:ZYNQ_GMAC_TSR]`
- `[zynq_gmac.h:ZYNQ_GMAC_RBQB]`
- `[zynq_gmac.h:ZYNQ_GMAC_TBQB]`
- `[zynq_gmac.h:ZYNQ_GMAC_RSR]`
- `[zynq_gmac.h:ZYNQ_GMAC_ISR]`
- `[zynq_gmac.h:ZYNQ_GMAC_IER]`
- `[zynq_gmac.h:ZYNQ_GMAC_IDR]`
- `[zynq_memorymap.h:ZYNQ_MPSOC_UART0_ADDR]`
- `[zynq_memorymap.h:ZYNQ_MPSOC_UART1_ADDR]`
- `[zynq_memorymap.h:ZYNQ_MPSOC_I2C0_ADDR]`
- `[zynq_memorymap.h:ZYNQ_MPSOC_I2C1_ADDR]`
- `[zynq_memorymap.h:ZYNQ_MPSOC_SPI0_ADDR]`
- `[zynq_memorymap.h:ZYNQ_MPSOC_SPI1_ADDR]`
- `[zynq_memorymap.h:ZYNQ_MPSOC_CAN0_ADDR]`
- `[zynq_memorymap.h:ZYNQ_MPSOC_CAN1_ADDR]`
- `[zynq_memorymap.h:ZYNQ_MPSOC_GPIO_ADDR]`
- `[zynq_memorymap.h:ZYNQ_MPSOC_GEM0_ADDR]`
- `[zynq_memorymap.h:ZYNQ_MPSOC_GEM1_ADDR]`
- `[zynq_memorymap.h:ZYNQ_MPSOC_GEM2_ADDR]`
- `[zynq_pll.h:mpsoc_clk_rate_get]`
- `[zynq_pll.h:mpsoc_clk_rate_set]`
- `[zynq_pll.h:mpsoc_clk]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
