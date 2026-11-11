# hardware (`nuttx/arch/arm/src/rp23xx/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/rp23xx/hardware`, providing 45 header file(s) and 0 source file(s) (including `rp23xx_accessctrl.h`, `rp23xx_adc.h`, `rp23xx_bootram.h`, `rp23xx_busctrl.h`).

## Interface
- `[rp23xx_accessctrl.h:RP23XX_ACCESSCTRL_LOCK_OFFSET]`
- `[rp23xx_accessctrl.h:RP23XX_ACCESSCTRL_FORCE_CORE_NS_OFFSET]`
- `[rp23xx_accessctrl.h:RP23XX_ACCESSCTRL_CFGRESET_OFFSET]`
- `[rp23xx_accessctrl.h:RP23XX_ACCESSCTRL_GPIO_NSMASK0_OFFSET]`
- `[rp23xx_accessctrl.h:RP23XX_ACCESSCTRL_GPIO_NSMASK1_OFFSET]`
- `[rp23xx_accessctrl.h:RP23XX_ACCESSCTRL_ROM_OFFSET]`
- `[rp23xx_accessctrl.h:RP23XX_ACCESSCTRL_XIP_MAIN_OFFSET]`
- `[rp23xx_accessctrl.h:RP23XX_ACCESSCTRL_SRAM0_OFFSET]`
- `[rp23xx_accessctrl.h:RP23XX_ACCESSCTRL_SRAM1_OFFSET]`
- `[rp23xx_accessctrl.h:RP23XX_ACCESSCTRL_SRAM2_OFFSET]`
- `[rp23xx_accessctrl.h:RP23XX_ACCESSCTRL_SRAM3_OFFSET]`
- `[rp23xx_accessctrl.h:RP23XX_ACCESSCTRL_SRAM4_OFFSET]`
- `[rp23xx_adc.h:RP23XX_ADC_CS_OFFSET]`
- `[rp23xx_adc.h:RP23XX_ADC_RESULT_OFFSET]`
- `[rp23xx_adc.h:RP23XX_ADC_FCS_OFFSET]`
- `[rp23xx_adc.h:RP23XX_ADC_FIFO_OFFSET]`
- `[rp23xx_adc.h:RP23XX_ADC_DIV_OFFSET]`
- `[rp23xx_adc.h:RP23XX_ADC_INTR_OFFSET]`
- `[rp23xx_adc.h:RP23XX_ADC_INTE_OFFSET]`
- `[rp23xx_adc.h:RP23XX_ADC_INTF_OFFSET]`
- `[rp23xx_adc.h:RP23XX_ADC_INTS_OFFSET]`
- `[rp23xx_adc.h:RP23XX_ADC_CS]`
- `[rp23xx_adc.h:RP23XX_ADC_RESULT]`
- `[rp23xx_adc.h:RP23XX_ADC_FCS]`
- `[rp23xx_bootram.h:RP23XX_BOOTRAM_WRITE_ONCE_OFFSET]`
- `[rp23xx_bootram.h:RP23XX_BOOTRAM_BOOTLOCK_STAT_OFFSET]`
- `[rp23xx_bootram.h:RP23XX_BOOTRAM_BOOTLOCK_OFFSET]`
- `[rp23xx_bootram.h:RP23XX_BOOTRAM_WRITE_ONCE]`
- `[rp23xx_bootram.h:RP23XX_BOOTRAM_BOOTLOCK_STAT]`
- `[rp23xx_bootram.h:RP23XX_BOOTRAM_BOOTLOCK]`

## Invariants
- None

## Side Effects
- `[rp23xx_memorymap.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[rp23xx_memorymap.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers

## Verification
- Run: `make test`
