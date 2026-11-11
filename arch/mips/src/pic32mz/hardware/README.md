# hardware (`nuttx/arch/mips/src/pic32mz/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/mips/src/pic32mz/hardware`, providing 25 header file(s) and 0 source file(s) (including `pic32mz_dma.h`, `pic32mz_ethernet.h`, `pic32mz_features.h`, `pic32mz_i2c.h`).

## Interface
- `[pic32mz_dma.h:PIC32MZ_DMACHn_OFFSET]`
- `[pic32mz_dma.h:PIC32MZ_DMACH0_OFFSET]`
- `[pic32mz_dma.h:PIC32MZ_DMACH1_OFFSET]`
- `[pic32mz_dma.h:PIC32MZ_DMACH2_OFFSET]`
- `[pic32mz_dma.h:PIC32MZ_DMACH3_OFFSET]`
- `[pic32mz_dma.h:PIC32MZ_DMACH4_OFFSET]`
- `[pic32mz_dma.h:PIC32MZ_DMACH5_OFFSET]`
- `[pic32mz_dma.h:PIC32MZ_DMACH6_OFFSET]`
- `[pic32mz_dma.h:PIC32MZ_DMACH7_OFFSET]`
- `[pic32mz_dma.h:PIC32MZ_DMA_CON_OFFSET]`
- `[pic32mz_dma.h:PIC32MZ_DMA_CONCLR_OFFSET]`
- `[pic32mz_dma.h:PIC32MZ_DMA_CONSET_OFFSET]`
- `[pic32mz_ethernet.h:pic32mz_txlinear_s]`
- `[pic32mz_ethernet.h:pic32mz_txdesc_s]`
- `[pic32mz_ethernet.h:pic32mz_rxlinear_s]`
- `[pic32mz_ethernet.h:pic32mz_rxdesc_s]`
- `[pic32mz_ethernet.h:PIC32MZ_ETH_CON1_OFFSET]`
- `[pic32mz_ethernet.h:PIC32MZ_ETH_CON1CLR_OFFSET]`
- `[pic32mz_ethernet.h:PIC32MZ_ETH_CON1SET_OFFSET]`
- `[pic32mz_ethernet.h:PIC32MZ_ETH_CON1INV_OFFSET]`
- `[pic32mz_ethernet.h:PIC32MZ_ETH_CON2_OFFSET]`
- `[pic32mz_ethernet.h:PIC32MZ_ETH_CON2CLR_OFFSET]`
- `[pic32mz_ethernet.h:PIC32MZ_ETH_CON2SET_OFFSET]`
- `[pic32mz_ethernet.h:PIC32MZ_ETH_CON2INV_OFFSET]`
- `[pic32mz_ethernet.h:PIC32MZ_ETH_TXST_OFFSET]`
- `[pic32mz_ethernet.h:PIC32MZ_ETH_TXSTCLR_OFFSET]`
- `[pic32mz_ethernet.h:PIC32MZ_ETH_TXSTSET_OFFSET]`
- `[pic32mz_ethernet.h:PIC32MZ_ETH_TXSTINV_OFFSET]`
- `[pic32mz_i2c.h:PIC32MZ_I2Cn_OFFSET]`
- `[pic32mz_i2c.h:PIC32MZ_I2C1_OFFSET]`

## Invariants
- `[pic32mz_features.h:#error]` Compile-time guard: Unknown PIC32MZ family
- `[pic32mz_memorymap.h:#error]` Compile-time guard: Unknown PIC32MZ family
- `[pic32mz_pps.h:#error]` Compile-time guard: Unknown PIC32MZ family

## Side Effects
- None

## Verification
- Run: `make test`
