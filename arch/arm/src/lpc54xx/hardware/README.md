# hardware (`nuttx/arch/arm/src/lpc54xx/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/lpc54xx/hardware`, providing 24 header file(s) and 0 source file(s) (including `lpc546x_memorymap.h`, `lpc546x_pinmux.h`, `lpc54_dma.h`, `lpc54_emc.h`).

## Interface
- `[lpc546x_memorymap.h:LPC54_FLASH_BASE]`
- `[lpc546x_memorymap.h:LPC54_BOOTROM_BASE]`
- `[lpc546x_memorymap.h:LPC54_SRAMX_BASE]`
- `[lpc546x_memorymap.h:LPC54_SPIFLASH_BASE]`
- `[lpc546x_memorymap.h:LPC54_SRAM_BASE]`
- `[lpc546x_memorymap.h:LPC54_SRAMBB_BASE]`
- `[lpc546x_memorymap.h:LPC54_APB0_BASE]`
- `[lpc546x_memorymap.h:LPC54_APB1_BASE]`
- `[lpc546x_memorymap.h:LPC54_APB2_BASE]`
- `[lpc546x_memorymap.h:LPC54_AHB_BASE]`
- `[lpc546x_memorymap.h:LPC54_USBSRAM_BASE]`
- `[lpc546x_memorymap.h:LPC54_PERIPHBB_BASE]`
- `[lpc546x_pinmux.h:GPIO_ADC0_0]`
- `[lpc546x_pinmux.h:GPIO_ADC0_1]`
- `[lpc546x_pinmux.h:GPIO_ADC0_2]`
- `[lpc546x_pinmux.h:GPIO_ADC0_3]`
- `[lpc546x_pinmux.h:GPIO_ADC0_4]`
- `[lpc546x_pinmux.h:GPIO_ADC0_5]`
- `[lpc546x_pinmux.h:GPIO_ADC0_6]`
- `[lpc546x_pinmux.h:GPIO_ADC0_7]`
- `[lpc546x_pinmux.h:GPIO_ADC0_8]`
- `[lpc546x_pinmux.h:GPIO_ADC0_9]`
- `[lpc546x_pinmux.h:GPIO_ADC0_10]`
- `[lpc546x_pinmux.h:GPIO_ADC0_11]`
- `[lpc54_dma.h:lpc54_dmachan_desc_s]`
- `[lpc54_dma.h:LPC54_DMA_NCHANNELS]`
- `[lpc54_dma.h:LPC54_DMA_MAXXFRS]`
- `[lpc54_dma.h:LPC54_DMA_CTRL_OFFSET]`
- `[lpc54_dma.h:LPC54_DMA_INTSTAT_OFFSET]`
- `[lpc54_dma.h:LPC54_DMA_SRAMBASE_OFFSET]`

## Invariants
- `[lpc54_memorymap.h:#error]` Compile-time guard: Unsupported LPC54 family
- `[lpc54_pinmux.h:#error]` Compile-time guard: Unsupported LPC54 family

## Side Effects
- None

## Verification
- Run: `make test`
