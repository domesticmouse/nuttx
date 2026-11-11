# lpc43xx (`nuttx/arch/arm/src/lpc43xx`)

## Overview
Hardware abstraction and architecture package for `lpc43xx` (LPC43xx Configuration Options; LPC43xx Peripheral Support) under `nuttx/arch/arm/src/lpc43xx`, providing 35 header file(s) and 36 source file(s) (including `chip.h`, `lpc43_adc.h`, `lpc43_can.h`, `lpc43_ccu.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/lpc43xx/hardware`, providing 43 header file(s) and 0 source file(s) (including `lpc4310203050_memorymap.h`, `lpc4310203050_pinconfig.h`, `lpc4337jet100_pinconfig.h`, `lpc435357_memorymap.h`).
- `spifi`: [./spifi/README.md](./spifi/README.md) - Architectural grouping for `nuttx/arch/arm/src/lpc43xx/spifi`, coordinating 2 component subdirectories (`inc`, `src`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[lpc43_adc.h:lpc43_adcinitialize]`
- `[lpc43_can.h:lpc43_caninitialize]`
- `[lpc43_cgu.h:lpc43_pll0usbdisable]`
- `[lpc43_cgu.h:lpc43_pll0usbenable]`
- `[lpc43_cgu.h:lpc43_pll0usbconfig]`
- `[lpc43_cgu.h:lpc43_clockconfig]`
- `[lpc43_config.h:HAVE_UART]`
- `[lpc43_config.h:HAVE_SERIAL_CONSOLE]`
- `[lpc43_config.h:HAVE_RS485]`
- `[lpc43_dac.h:lpc43_dacinitialize]`
- `[lpc43_ehci.h:lpc43_ehci_initialize]`
- `[lpc43_emc.h:lpc43_emcinit]`
- `[lpc43_emc.h:EMC_CS0]`
- `[lpc43_emc.h:EMC_CS1]`
- `[lpc43_emc.h:EMC_CS2]`
- `[lpc43_emc.h:EMC_CS3]`
- `[lpc43_emc.h:EMC_DYNCS0]`
- `[lpc43_emc.h:EMC_DYNCS1]`
- `[lpc43_emc.h:EMC_DYNCS2]`
- `[lpc43_emc.h:EMC_DYNCS3]`
- `[lpc43_ethernet.h:lpc43_phy_boardinitialize]`
- `[lpc43_gpdma.h:lpc43_dmachannel]`
- `[lpc43_gpdma.h:lpc43_dmafree]`
- `[lpc43_gpdma.h:lpc43_dmasetup]`
- `[lpc43_gpdma.h:lpc43_dmastart]`
- `[lpc43_gpdma.h:lpc43_dmastop]`
- `[lpc43_gpdma.h:lpc43_dmasample]`
- `[lpc43_gpdma.h:lpc43_dmadump]`
- `[lpc43_gpdma.h:lpc43_dmaglobalregs_s]`
- [./hardware/README.md](./hardware/README.md)
- [./spifi/README.md](./spifi/README.md)

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported LPC43xx chip
- `[lpc43_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc43_adc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc43_adc.c:#error]` Compile-time configuration constraint: Set CONFIG_LPC43_ADC0_FREQ != 0 if CONFIG_LPC43_ADC0_USE_TIMER
- `[lpc43_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc43_allocateheap.c:#error]` Compile-time configuration constraint: CONFIG_RAM_START must be set to the base address of RAM bank 0
- `[lpc43_can.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc43_can.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc43_cgu.c:#error]` Compile-time configuration constraint: board.h must provide the LPC43xx cystal input frequency (BOARD_XTAL_FREQUENCY)
- `[lpc43_crypto.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc43_dac.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc43_ehci.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[lpc43_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc43_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc43_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[lpc43_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[lpc43_adc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[lpc43_can.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc43_can.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc43_can.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[lpc43_can.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[lpc43_can.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[lpc43_cgu.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc43_cgu.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
