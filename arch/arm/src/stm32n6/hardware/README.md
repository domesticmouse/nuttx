# hardware (`nuttx/arch/arm/src/stm32n6/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32n6/hardware`, providing 12 header file(s) and 0 source file(s) (including `stm32_dmasigmap.h`, `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`).

## Interface
- `[stm32n6xxx_bsec.h:STM32_BSEC_DBGCR_OFFSET]`
- `[stm32n6xxx_bsec.h:STM32_BSEC_AP_UNLOCK_OFFSET]`
- `[stm32n6xxx_bsec.h:STM32_BSEC_HDPLSR_OFFSET]`
- `[stm32n6xxx_bsec.h:STM32_BSEC_DBGCR]`
- `[stm32n6xxx_bsec.h:STM32_BSEC_AP_UNLOCK]`
- `[stm32n6xxx_bsec.h:STM32_BSEC_HDPLSR]`
- `[stm32n6xxx_bsec.h:BSEC_DBGCR_UNLOCK]`
- `[stm32n6xxx_bsec.h:BSEC_DBGCR_AUTH_HDPL_SHIFT]`
- `[stm32n6xxx_bsec.h:BSEC_DBGCR_AUTH_SEC]`
- `[stm32n6xxx_bsec.h:BSEC_AP_UNLOCK_UNLOCK]`
- `[stm32n6xxx_bsec.h:BSEC_HDPLSR_HDPL_MASK]`
- `[stm32n6xxx_dmasigmap.h:GPDMA_REQ_JPEG_RX]`
- `[stm32n6xxx_dmasigmap.h:GPDMA_REQ_JPEG_TX]`
- `[stm32n6xxx_dmasigmap.h:GPDMA_REQ_XSPI1]`
- `[stm32n6xxx_dmasigmap.h:GPDMA_REQ_XSPI2]`
- `[stm32n6xxx_dmasigmap.h:GPDMA_REQ_XSPI3]`
- `[stm32n6xxx_dmasigmap.h:GPDMA_REQ_FMC2_TXRX]`
- `[stm32n6xxx_dmasigmap.h:GPDMA_REQ_FMC2_BCH]`
- `[stm32n6xxx_dmasigmap.h:GPDMA_REQ_ADC1]`
- `[stm32n6xxx_dmasigmap.h:GPDMA_REQ_ADC2]`
- `[stm32n6xxx_dmasigmap.h:GPDMA_REQ_CRYP_IN]`
- `[stm32n6xxx_dmasigmap.h:GPDMA_REQ_CRYP_OUT]`
- `[stm32n6xxx_dmasigmap.h:GPDMA_REQ_SAES_OUT]`
- `[stm32n6xxx_memorymap.h:STM32_CODE_BASE]`
- `[stm32n6xxx_memorymap.h:STM32_SRAM_BASE]`
- `[stm32n6xxx_memorymap.h:STM32_PERIPH_BASE]`
- `[stm32n6xxx_memorymap.h:STM32_CORTEX_BASE]`
- `[stm32n6xxx_memorymap.h:STM32_REGION_MASK]`
- `[stm32n6xxx_memorymap.h:STM32_IS_SRAM]`
- `[stm32n6xxx_memorymap.h:STM32_SRAM1_BASE]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
