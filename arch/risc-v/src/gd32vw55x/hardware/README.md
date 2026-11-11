# hardware (`nuttx/arch/risc-v/src/gd32vw55x/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/gd32vw55x/hardware`, providing 17 header file(s) and 0 source file(s) (including `gd32vw55x_adc.h`, `gd32vw55x_crc.h`, `gd32vw55x_dma.h`, `gd32vw55x_eclic.h`).

## Interface
- `[gd32vw55x_adc.h:GD32VW55X_ADC_NCHANNELS]`
- `[gd32vw55x_adc.h:GD32VW55X_ADC_MAX_SAMPLES]`
- `[gd32vw55x_adc.h:GD32VW55X_ADC_STAT_OFFSET]`
- `[gd32vw55x_adc.h:GD32VW55X_ADC_CTL0_OFFSET]`
- `[gd32vw55x_adc.h:GD32VW55X_ADC_CTL1_OFFSET]`
- `[gd32vw55x_adc.h:GD32VW55X_ADC_SAMPT0_OFFSET]`
- `[gd32vw55x_adc.h:GD32VW55X_ADC_SAMPT1_OFFSET]`
- `[gd32vw55x_adc.h:GD32VW55X_ADC_IOFF0_OFFSET]`
- `[gd32vw55x_adc.h:GD32VW55X_ADC_IOFF1_OFFSET]`
- `[gd32vw55x_adc.h:GD32VW55X_ADC_IOFF2_OFFSET]`
- `[gd32vw55x_adc.h:GD32VW55X_ADC_IOFF3_OFFSET]`
- `[gd32vw55x_adc.h:GD32VW55X_ADC_WDHT_OFFSET]`
- `[gd32vw55x_crc.h:GD32VW55X_CRC_DATA_OFFSET]`
- `[gd32vw55x_crc.h:GD32VW55X_CRC_FDATA_OFFSET]`
- `[gd32vw55x_crc.h:GD32VW55X_CRC_CTL_OFFSET]`
- `[gd32vw55x_crc.h:GD32VW55X_CRC_DATA]`
- `[gd32vw55x_crc.h:GD32VW55X_CRC_FDATA]`
- `[gd32vw55x_crc.h:GD32VW55X_CRC_CTL]`
- `[gd32vw55x_crc.h:CRC_DATA_RESET]`
- `[gd32vw55x_crc.h:CRC_FDATA_SHIFT]`
- `[gd32vw55x_crc.h:CRC_FDATA_MASK]`
- `[gd32vw55x_crc.h:CRC_CTL_RST]`
- `[gd32vw55x_dma.h:GD32VW55X_NDMA]`
- `[gd32vw55x_dma.h:GD32VW55X_NDMA_CHANNELS]`
- `[gd32vw55x_dma.h:GD32VW55X_NDMA_SUBPERIPHS]`
- `[gd32vw55x_dma.h:GD32_DMA_INTF0_OFFSET]`
- `[gd32vw55x_dma.h:GD32_DMA_INTF1_OFFSET]`
- `[gd32vw55x_dma.h:GD32_DMA_INTC0_OFFSET]`
- `[gd32vw55x_dma.h:GD32_DMA_INTC1_OFFSET]`
- `[gd32vw55x_dma.h:GD32_DMA_CH0CTL_OFFSET]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
