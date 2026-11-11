# samv7 (`nuttx/arch/arm/src/samv7`)

## Overview
Hardware abstraction and architecture package for `samv7` (SAMV7 Configuration Options; SAMV7 Peripheral Selection) under `nuttx/arch/arm/src/samv7`, providing 41 header file(s) and 47 source file(s) (including `chip.h`, `sam_1wire.h`, `sam_afec.h`, `sam_chipid.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/samv7/hardware`, providing 34 header file(s) and 0 source file(s) (including `sam_afec.h`, `sam_chipid.h`, `sam_dacc.h`, `sam_eefc.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV7M_DCACHE_LINESIZE]`
- `[chip.h:ARMV7M_ICACHE_LINESIZE]`
- `[sam_1wire.h:sam_1wireinitialize]`
- `[sam_afec.h:sam_afec_initialize]`
- `[sam_afec.h:AFEC0]`
- `[sam_afec.h:AFEC1]`
- `[sam_chipid.h:sam_has_revb_periphs]`
- `[sam_clockconfig.h:sam_clockconfig]`
- `[sam_clockconfig.h:sam_usbclock]`
- `[sam_config.h:HAVE_UART_DEVICE]`
- `[sam_config.h:HAVE_SERIAL_CONSOLE]`
- `[sam_dac.h:sam_dac_initialize]`
- `[sam_dac.h:CONFIG_SAMV7_DAC_DMA_BUFFER_SIZE]`
- `[sam_dac.h:CONFIG_SAMV7_DAC_TRIGGER_FREQUENCY]`
- `[sam_dac.h:CONFIG_SAMV7_DAC_PRESCAL]`
- `[sam_dac.h:CONFIG_SAMV7_DAC_TRIGGER_SELECT]`
- `[sam_eefc.h:sam_eefc_writefmr]`
- `[sam_eefc.h:sam_eefc_command]`
- `[sam_eefc.h:sam_eefc_readsequence]`
- `[sam_eefc.h:sam_eefc_initaccess]`
- `[sam_eefc.h:sam_eefc_unlock]`
- `[sam_eefc.h:SAM_EFC_ACCESS_MODE_128]`
- `[sam_eefc.h:SAM_EFC_ACCESS_MODE_64]`
- `[sam_ethernet.h:sam_emac_initialize]`
- `[sam_ethernet.h:sam_emac_setmacaddr]`
- `[sam_ethernet.h:sam_phy_boardinitialize]`
- `[sam_ethernet.h:SAMV7_PHY_DM9161]`
- `[sam_ethernet.h:SAMV7_PHY_LAN8700]`
- `[sam_ethernet.h:SAMV7_PHY_KSZ8051]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[sam_ethernet.h:#error]` Compile-time guard: EMAC0 and EMAC2 cannot both be ETH0
- `[sam_gpio.h:DEBUGASSERT]` Enforces runtime precondition assertions in inline/macro helpers
- `[sam_periphclks.h:#error]` Compile-time guard: Unrecognized SAMV7 architecture
- `[sam_1wire.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sam_1wire.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sam_afec.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sam_afec.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sam_afec.c:#error]` Compile-time configuration constraint: CONFIG_SAMV7_AFEC_DMASAMPLES must be defined
- `[sam_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sam_allocateheap.c:#error]` Compile-time configuration constraint: CONFIG_RAM_END is beyond the end of SRAM
- `[sam_clockconfig.c:#error]` Compile-time configuration constraint: ERROR: Unrecognized MAINSOSC frequency
- `[sam_dac.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[same70_periphclks.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[samv71_periphclks.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[sam_1wire.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sam_1wire.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[sam_1wire.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[sam_1wire.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[sam_afec.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sam_afec.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[sam_afec.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[sam_afec.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[sam_afec.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[sam_afec.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)

## Verification
- Run: `make test`
