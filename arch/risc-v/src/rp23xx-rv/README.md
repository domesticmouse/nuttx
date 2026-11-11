# rp23xx-rv (`nuttx/arch/risc-v/src/rp23xx-rv`)

## Overview
Hardware abstraction and architecture package for `rp23xx-rv` (RP23XX Configuration Options) under `nuttx/arch/risc-v/src/rp23xx-rv`, providing 21 header file(s) and 26 source file(s) (including `chip.h`, `rp23xx_adc.h`, `rp23xx_clock.h`, `rp23xx_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/rp23xx-rv/hardware`, providing 44 header file(s) and 0 source file(s) (including `rp23xx_accessctrl.h`, `rp23xx_adc.h`, `rp23xx_bootram.h`, `rp23xx_busctrl.h`).

## Interface
- `[rp23xx_adc.h:rp23xx_adc_setup]`
- `[rp23xx_clock.h:rp23xx_clockconfig]`
- `[rp23xx_clock.h:RP23XX_TICK_NUM]`
- `[rp23xx_config.h:HAVE_UART]`
- `[rp23xx_config.h:HAVE_SERIAL_CONSOLE]`
- `[rp23xx_config.h:HAVE_CONSOLE]`
- `[rp23xx_dmac.h:rp23xx_dmachannel]`
- `[rp23xx_dmac.h:rp23xx_dmafree]`
- `[rp23xx_dmac.h:rp23xx_rxdmasetup]`
- `[rp23xx_dmac.h:rp23xx_txdmasetup]`
- `[rp23xx_dmac.h:rp23xx_ctrl_dmasetup]`
- `[rp23xx_dmac.h:rp23xx_dma_ctrl_blk_ctrl]`
- `[rp23xx_dmac.h:rp23xx_dmastart]`
- `[rp23xx_dmac.h:rp23xx_dmastop]`
- `[rp23xx_dmac.h:rp23xx_dma_register]`
- `[rp23xx_dmac.h:dma_config_t]`
- `[rp23xx_dmac.h:dma_control_block_t]`
- `[rp23xx_dmac.h:DMA_HANDLE]`
- `[rp23xx_dmac.h:RP23XX_DMA_NCHANNELS]`
- `[rp23xx_dmac.h:RP23XX_DMA_SIZE_BYTE]`
- `[rp23xx_dmac.h:RP23XX_DMA_SIZE_HALFWORD]`
- `[rp23xx_dmac.h:RP23XX_DMA_SIZE_WORD]`
- `[rp23xx_dmac.h:RP23XX_DMA_CTRL_BLOCK_END]`
- `[rp23xx_gpio.h:rp23xx_gpio_get_function_pin]`
- `[rp23xx_gpio.h:rp23xx_gpio_set_function]`
- `[rp23xx_gpio.h:rp23xx_gpio_set_pulls]`
- `[rp23xx_gpio.h:rp23xx_gpio_init]`
- `[rp23xx_gpio.h:rp23xx_gpio_irq_attach]`
- `[rp23xx_gpio.h:rp23xx_gpio_enable_irq]`
- `[rp23xx_gpio.h:rp23xx_gpio_disable_irq]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[rp23xx_gpio.h:DEBUGASSERT]` Enforces runtime precondition assertions in inline/macro helpers
- `[rp23xx_pio.h:DEBUGASSERT]` Enforces runtime precondition assertions in inline/macro helpers
- `[rp23xx_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rp23xx_adc.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[rp23xx_clock.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[rp23xx_dmac.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rp23xx_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rp23xx_heaps.c:#error]` Compile-time configuration constraint: cannot use CONFIG_MM_KERNEL_HEAP with single heap
- `[rp23xx_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rp23xx_i2c.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[rp23xx_i2c.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[rp23xx_i2c_slave.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[rp23xx_gpio.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[rp23xx_gpio.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[rp23xx_pio.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[rp23xx_pio.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[rp23xx_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rp23xx_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rp23xx_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[rp23xx_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[rp23xx_adc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[rp23xx_clock.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rp23xx_clock.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rp23xx_cpustart.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
