# hardware (`nuttx/arch/arm/src/stm32f7/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32f7/hardware`, providing 55 header file(s) and 0 source file(s) (including `stm32_adc.h`, `stm32_can.h`, `stm32_dma.h`, `stm32_dma2d.h`).

## Interface
- `[stm32_can.h:CAN_TXMBOX1]`
- `[stm32_can.h:CAN_TXMBOX2]`
- `[stm32_can.h:CAN_TXMBOX3]`
- `[stm32_can.h:CAN_RXMBOX1]`
- `[stm32_can.h:CAN_RXMBOX2]`
- `[stm32_can.h:CAN_NFILTERS]`
- `[stm32_can.h:STM32_CAN_MCR_OFFSET]`
- `[stm32_can.h:STM32_CAN_MSR_OFFSET]`
- `[stm32_can.h:STM32_CAN_TSR_OFFSET]`
- `[stm32_can.h:STM32_CAN_RFR_OFFSET]`
- `[stm32_can.h:STM32_CAN_RF0R_OFFSET]`
- `[stm32_can.h:STM32_CAN_RF1R_OFFSET]`
- `[stm32_dma2d.h:STM32_DMA2D_NCLUT]`
- `[stm32_dma2d.h:STM32_DMA2D_CR_OFFSET]`
- `[stm32_dma2d.h:STM32_DMA2D_ISR_OFFSET]`
- `[stm32_dma2d.h:STM32_DMA2D_IFCR_OFFSET]`
- `[stm32_dma2d.h:STM32_DMA2D_FGMAR_OFFSET]`
- `[stm32_dma2d.h:STM32_DMA2D_FGOR_OFFSET]`
- `[stm32_dma2d.h:STM32_DMA2D_BGMAR_OFFSET]`
- `[stm32_dma2d.h:STM32_DMA2D_BGOR_OFFSET]`
- `[stm32_dma2d.h:STM32_DMA2D_FGPFCCR_OFFSET]`
- `[stm32_dma2d.h:STM32_DMA2D_FGCOLR_OFFSET]`
- `[stm32_dma2d.h:STM32_DMA2D_BGPFCCR_OFFSET]`
- `[stm32_dma2d.h:STM32_DMA2D_BGCOLR_OFFSET]`
- `[stm32_ethernet.h:eth_txdesc_s]`
- `[stm32_ethernet.h:eth_rxdesc_s]`
- `[stm32_ethernet.h:STM32_ETH_MACCR_OFFSET]`
- `[stm32_ethernet.h:STM32_ETH_MACFFR_OFFSET]`
- `[stm32_ethernet.h:STM32_ETH_MACHTHR_OFFSET]`
- `[stm32_ethernet.h:STM32_ETH_MACHTLR_OFFSET]`

## Invariants
- `[stm32_adc.h:#error]` Compile-time guard: Unsupported STM32 F7 sub family
- `[stm32_dma.h:#error]` Compile-time guard: Unsupported STM32 F7 part
- `[stm32_flash.h:#error]` Compile-time guard: Unsupported STM32 F7 part
- `[stm32_gpio.h:#error]` Compile-time guard: Unsupported STM32 F7 part
- `[stm32_i2c.h:#error]` Compile-time guard: Unsupported STM32 F7 sub family
- `[stm32_memorymap.h:#error]` Compile-time guard: Unsupported STM32 F7 memory map
- `[stm32_pinmap.h:#error]` Compile-time guard: Unsupported STM32 F7 Pin map
- `[stm32_pwr.h:#error]` Compile-time guard: Unsupported STM32 F7 part
- `[stm32_rcc.h:#error]` Compile-time guard: Unsupported STM32 F7 part
- `[stm32_sdmmc.h:#error]` Compile-time guard: Unsupported STM32 F7 part
- `[stm32_spi.h:#error]` Compile-time guard: Unsupported STM32 F7 sub family
- `[stm32_syscfg.h:#error]` Compile-time guard: Unsupported STM32 F7 part

## Side Effects
- None

## Verification
- Run: `make test`
