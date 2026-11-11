# efm32 (`nuttx/arch/arm/src/efm32`)

## Overview
Hardware abstraction and architecture package for `efm32` (EFM32 Configuration Options; EFM32 Peripheral Support) under `nuttx/arch/arm/src/efm32`, providing 17 header file(s) and 22 source file(s) (including `chip.h`, `efm32_adc.h`, `efm32_bitband.h`, `efm32_clockconfig.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/efm32/hardware`, providing 32 header file(s) and 0 source file(s) (including `efm32_acmp.h`, `efm32_adc.h`, `efm32_aes.h`, `efm32_burtc.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[efm32_adc.h:efm32_adcinitialize]`
- `[efm32_adc.h:ADC1_HAVE_TIMER]`
- `[efm32_adc.h:ADC1_TIMER_BASE]`
- `[efm32_adc.h:ADC1_TIMER_PCLK_FREQUENCY]`
- `[efm32_bitband.h:bitband_set_peripheral]`
- `[efm32_bitband.h:bitband_get_peripheral]`
- `[efm32_bitband.h:bitband_set_sram]`
- `[efm32_bitband.h:bitband_get_sram]`
- `[efm32_clockconfig.h:efm32_clockconfig]`
- `[efm32_config.h:HAVE_UART_DEVICE]`
- `[efm32_config.h:HAVE_SPI_DEVICE]`
- `[efm32_config.h:HAVE_LEUART_DEVICE]`
- `[efm32_config.h:HAVE_UART_CONSOLE]`
- `[efm32_config.h:HAVE_LEUART_CONSOLE]`
- `[efm32_dma.h:efm32_dmachannel]`
- `[efm32_dma.h:efm32_dmafree]`
- `[efm32_dma.h:efm32_rxdmasetup]`
- `[efm32_dma.h:efm32_txdmasetup]`
- `[efm32_dma.h:efm32_dmastart]`
- `[efm32_dma.h:efm32_dmastop]`
- `[efm32_dma.h:efm32_dmasample]`
- `[efm32_dma.h:efm32_dmadump]`
- `[efm32_dma.h:efm32_dmaregs_s]`
- `[efm32_dma.h:DMA_HANDLE]`
- `[efm32_dma.h:dma_config_t]`
- `[efm32_dma.h:EFM32_DMA_SIGSEL_SHIFT]`
- `[efm32_dma.h:EFM32_DMA_SIGSEL_MASK]`
- `[efm32_dma.h:EFM32_DMA_SIGSEL]`
- `[efm32_dma.h:EFM32_DMA_SOURCSEL_SHIFT]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[efm32_adc.h:#error]` Compile-time guard: CONFIG_EFM32_ADC1_SAMPLE_FREQUENCY not defined
- `[efm32_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[efm32_adc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[efm32_bitband.c:#error]` Compile-time configuration constraint: EFM32_BITBAND_PER_BASE not declared bitband may be not supported?
- `[efm32_clockconfig.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[efm32_clockconfig.c:#error]` Compile-time configuration constraint: HFCLK divisor not yet supported
- `[efm32_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[efm32_dma.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[efm32_dma.c:#error]` Compile-time configuration constraint: Unknown descriptor table size
- `[efm32_flash.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[efm32_flash.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[efm32_flash.c:#error]` Compile-time configuration constraint: Flashing function should executed in ram

## Side Effects
- `[efm32_bitband.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[efm32_bitband.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[efm32_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[efm32_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[efm32_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[efm32_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[efm32_adc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[efm32_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[efm32_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[efm32_dma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[efm32_dma.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[efm32_dma.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
