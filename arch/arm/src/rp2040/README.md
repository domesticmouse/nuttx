# rp2040 (`nuttx/arch/arm/src/rp2040`)

## Overview
Hardware abstraction and architecture package for `rp2040` (RP2040 Configuration Options) under `nuttx/arch/arm/src/rp2040`, providing 23 header file(s) and 30 source file(s) (including `chip.h`, `rp2040_adc.h`, `rp2040_clock.h`, `rp2040_config.h`).

## Subdirectories & Boundaries
- `boot2`: [./boot2/README.md](./boot2/README.md) - Architectural grouping for `nuttx/arch/arm/src/rp2040/boot2`, coordinating 1 component subdirectories (`pico`).
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/rp2040/hardware`, providing 21 header file(s) and 0 source file(s) (including `rp2040_adc.h`, `rp2040_address_mapped.h`, `rp2040_clocks.h`, `rp2040_dma.h`).

## Interface
- `[chip.h:ARMV6M_PERIPHERAL_INTERRUPTS]`
- `[rp2040_adc.h:rp2040_adc_initialize]`
- `[rp2040_clock.h:rp2040_clockconfig]`
- `[rp2040_config.h:HAVE_UART]`
- `[rp2040_config.h:HAVE_SERIAL_CONSOLE]`
- `[rp2040_config.h:HAVE_CONSOLE]`
- `[rp2040_cyw43439.h:rp2040_cyw_setup]`
- `[rp2040_cyw43439.h:rp2040_cyw_remove]`
- `[rp2040_cyw43439.h:rp2040_gspi_t]`
- `[rp2040_cyw43439.h:cyw_pio_program_t]`
- `[rp2040_cyw43439.h:__BOARDS_ARM_RP2040_COMMON_INCLUDE_RP2040_CYW43439_H]`
- `[rp2040_dmac.h:rp2040_dmachannel]`
- `[rp2040_dmac.h:rp2040_dmafree]`
- `[rp2040_dmac.h:rp2040_rxdmasetup]`
- `[rp2040_dmac.h:rp2040_txdmasetup]`
- `[rp2040_dmac.h:rp2040_ctrl_dmasetup]`
- `[rp2040_dmac.h:rp2040_dma_ctrl_blk_ctrl]`
- `[rp2040_dmac.h:rp2040_dmastart]`
- `[rp2040_dmac.h:rp2040_dmastop]`
- `[rp2040_dmac.h:rp2040_dma_register]`
- `[rp2040_dmac.h:dma_config_t]`
- `[rp2040_dmac.h:dma_control_block_t]`
- `[rp2040_dmac.h:DMA_HANDLE]`
- `[rp2040_dmac.h:RP2040_DMA_NCHANNELS]`
- `[rp2040_dmac.h:RP2040_DMA_DREQ_PIO0_TX0]`
- `[rp2040_dmac.h:RP2040_DMA_DREQ_PIO0_TX1]`
- `[rp2040_dmac.h:RP2040_DMA_DREQ_PIO0_TX2]`
- `[rp2040_dmac.h:RP2040_DMA_DREQ_PIO0_TX3]`
- `[rp2040_dmac.h:RP2040_DMA_DREQ_PIO0_RX0]`
- `[rp2040_dmac.h:RP2040_DMA_DREQ_PIO0_RX1]`
- [./boot2/README.md](./boot2/README.md)
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[rp2040_gpio.h:DEBUGASSERT]` Enforces runtime precondition assertions in inline/macro helpers
- `[rp2040_pio.h:DEBUGASSERT]` Enforces runtime precondition assertions in inline/macro helpers
- `[rp2040_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rp2040_adc.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[rp2040_clock.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[rp2040_cyw43439.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[rp2040_dmac.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rp2040_flash_mtd.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[rp2040_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rp2040_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rp2040_i2c.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[rp2040_i2c.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[rp2040_gpio.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[rp2040_gpio.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[rp2040_pio.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[rp2040_pio.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[rp2040_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rp2040_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rp2040_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[rp2040_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[rp2040_adc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[rp2040_clock.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rp2040_clock.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rp2040_cpuindex.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
