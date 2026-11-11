# sama5 (`nuttx/arch/arm/src/sama5`)

## Overview
Hardware abstraction and architecture package for `sama5` (SAMA5 Configuration Options; SAMA5 Peripheral Support) under `nuttx/arch/arm/src/sama5`, providing 49 header file(s) and 63 source file(s) (including `chip.h`, `sam_adc.h`, `sam_boot.h`, `sam_can.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/sama5/hardware`, providing 60 header file(s) and 0 source file(s) (including `_sama5d2x_memorymap.h`, `_sama5d2x_pinmap.h`, `_sama5d2x_pio.h`, `_sama5d3x4x_pio.h`).

## Interface
- `[chip.h:L2CC_VBASE]`
- `[chip.h:ARMV7A_DCACHE_LINESIZE]`
- `[chip.h:ARMV7A_ICACHE_LINESIZE]`
- `[sam_adc.h:sam_adc_initialize]`
- `[sam_adc.h:sam_adc_lock]`
- `[sam_adc.h:sam_adc_unlock]`
- `[sam_adc.h:sam_adc_getreg]`
- `[sam_adc.h:sam_adc_putreg]`
- `[sam_adc.h:SAMA5_ADC_HAVE_CHANNELS]`
- `[sam_boot.h:sam_boardinitialize]`
- `[sam_can.h:sam_caninitialize]`
- `[sam_can.h:CONFIG_SAMA5_CAN0_NRECVMB]`
- `[sam_can.h:CONFIG_SAMA5_CAN1_NRECVMB]`
- `[sam_classd.h:sama5_classd_initialize]`
- `[sam_clockconfig.h:sam_clockconfig]`
- `[sam_clockconfig.h:board_norflash_config]`
- `[sam_config.h:SAMA5_HAVE_UART]`
- `[sam_config.h:SAMA5_HAVE_USART]`
- `[sam_config.h:SAMA5_HAVE_FLEXCOM_USART]`
- `[sam_config.h:SUPPRESS_CONSOLE_CONFIG]`
- `[sam_config.h:SAMA5_HAVE_DBGU_CONSOLE]`
- `[sam_config.h:SAMA5_HAVE_UART_CONSOLE]`
- `[sam_config.h:SAMA5_HAVE_USART_CONSOLE]`
- `[sam_dbgu.h:sam_dbgu_initialize]`
- `[sam_dbgu.h:sam_dbgu_register]`
- `[sam_dmac.h:sam_dmachannel]`
- `[sam_dmac.h:sam_dmaconfig]`
- `[sam_dmac.h:sam_dmafree]`
- `[sam_dmac.h:sam_dmatxsetup]`
- `[sam_dmac.h:sam_dmarxsetup]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[sam_adc.h:#error]` Compile-time guard: Work queue support is required (CONFIG_SCHED_WORKQUEUE)
- `[sam_can.h:#error]` Compile-time guard: CONFIG_SAMA5_CAN0_BAUD is not defined
- `[sam_config.h:#error]` Compile-time guard: Cannot have both USART and Flexcom USART
- `[sam_ethernet.h:#error]` Compile-time guard: GMAC and EMAC cannot both be ETH0
- `[sam_lcd.h:#error]` Compile-time guard: CONFIG_SAMA5_LCDC_FB_VBASE not aligned to 1MB boundary
- `[sam_memorymap.h:#error]` Compile-time guard: High vector remap cannot be performed if we are using a ROM page table
- `[sam_nand.h:#error]` Compile-time guard: DMA controller 0 (DMAC0) must be enabled to perform DMA transfers
- `[sam_periphclks.h:#error]` Compile-time guard: Unrecognized SAMA5 family
- `[sam_pio.h:#error]` Compile-time guard: Unrecognized SAMA5 architecture
- `[sam_pmecc.h:#error]` Compile-time guard: CONFIG_SAMA5_PMECC_GALOIS_TABLE512_ROMADDR is not defined
- `[sam_pwm.h:#error]` Compile-time guard: No PWM channels configured
- `[sam_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[sam_adc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[sam_adc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[sam_nand.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[sam_nand.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[sama5d2x_periphclks.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[sama5d2x_periphclks.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[sama5d3x_periphclks.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[sama5d3x_periphclks.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[sama5d4x_periphclks.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[sama5d4x_periphclks.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[sam_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sam_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
