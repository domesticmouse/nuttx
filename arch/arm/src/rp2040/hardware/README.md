# hardware (`nuttx/arch/arm/src/rp2040/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/rp2040/hardware`, providing 21 header file(s) and 0 source file(s) (including `rp2040_adc.h`, `rp2040_address_mapped.h`, `rp2040_clocks.h`, `rp2040_dma.h`).

## Interface
- `[rp2040_adc.h:RP2040_ADC_CS_OFFSET]`
- `[rp2040_adc.h:RP2040_ADC_RESULT_OFFSET]`
- `[rp2040_adc.h:RP2040_ADC_FCS_OFFSET]`
- `[rp2040_adc.h:RP2040_ADC_FIFO_OFFSET]`
- `[rp2040_adc.h:RP2040_ADC_DIV_OFFSET]`
- `[rp2040_adc.h:RP2040_ADC_INTR_OFFSET]`
- `[rp2040_adc.h:RP2040_ADC_INTE_OFFSET]`
- `[rp2040_adc.h:RP2040_ADC_INTF_OFFSET]`
- `[rp2040_adc.h:RP2040_ADC_INTS_OFFSET]`
- `[rp2040_adc.h:RP2040_ADC_CS]`
- `[rp2040_adc.h:RP2040_ADC_RESULT]`
- `[rp2040_adc.h:RP2040_ADC_FCS]`
- `[rp2040_address_mapped.h:REG_ALIAS_XOR_BITS]`
- `[rp2040_address_mapped.h:hw_alias_check_addr]`
- `[rp2040_address_mapped.h:hw_xor_alias_untyped]`
- `[rp2040_clocks.h:RP2040_CLOCKS_NDX_GPOUT0]`
- `[rp2040_clocks.h:RP2040_CLOCKS_NDX_GPOUT1]`
- `[rp2040_clocks.h:RP2040_CLOCKS_NDX_GPOUT2]`
- `[rp2040_clocks.h:RP2040_CLOCKS_NDX_GPOUT3]`
- `[rp2040_clocks.h:RP2040_CLOCKS_NDX_REF]`
- `[rp2040_clocks.h:RP2040_CLOCKS_NDX_SYS]`
- `[rp2040_clocks.h:RP2040_CLOCKS_NDX_PERI]`
- `[rp2040_clocks.h:RP2040_CLOCKS_NDX_USB]`
- `[rp2040_clocks.h:RP2040_CLOCKS_NDX_ADC]`
- `[rp2040_clocks.h:RP2040_CLOCKS_NDX_RTC]`
- `[rp2040_clocks.h:RP2040_CLOCKS_NDX_MAX]`
- `[rp2040_clocks.h:RP2040_CLOCKS_CLK_CTRL_OFFSET]`
- `[rp2040_dma.h:RP2040_DMA_READ_ADDR_OFFSET]`
- `[rp2040_dma.h:RP2040_DMA_WRITE_ADDR_OFFSET]`
- `[rp2040_dma.h:RP2040_DMA_TRANS_COUNT_OFFSET]`

## Invariants
- None

## Side Effects
- `[rp2040_memorymap.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[rp2040_memorymap.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers

## Verification
- Run: `make test`
