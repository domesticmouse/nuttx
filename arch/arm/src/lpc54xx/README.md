# lpc54xx (`nuttx/arch/arm/src/lpc54xx`)

## Overview
Hardware abstraction and architecture package for `lpc54xx` (LPC54xx Configuration Options; LPC54xx Peripheral Selection) under `nuttx/arch/arm/src/lpc54xx`, providing 25 header file(s) and 27 source file(s) (including `chip.h`, `lpc546x_enableclk.h`, `lpc546x_power.h`, `lpc546x_reset.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/lpc54xx/hardware`, providing 24 header file(s) and 0 source file(s) (including `lpc546x_memorymap.h`, `lpc546x_pinmux.h`, `lpc54_dma.h`, `lpc54_emc.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[lpc546x_enableclk.h:lpc54_periph0_enableclk]`
- `[lpc546x_enableclk.h:lpc54_periph1_enableclk]`
- `[lpc546x_enableclk.h:lpc54_periph2_enableclk]`
- `[lpc546x_enableclk.h:lpc54_asynch_enableclk]`
- `[lpc546x_enableclk.h:lpc54_periph0_disableclk]`
- `[lpc546x_enableclk.h:lpc54_periph1_disableclk]`
- `[lpc546x_enableclk.h:lpc54_periph2_disableclk]`
- `[lpc546x_enableclk.h:lpc54_asynch_disableclk]`
- `[lpc546x_enableclk.h:lpc54_periph0_isenabled]`
- `[lpc546x_enableclk.h:lpc54_periph1_isenabled]`
- `[lpc546x_enableclk.h:lpc54_periph2_isenabled]`
- `[lpc546x_enableclk.h:lpc54_asynch_isenabled]`
- `[lpc546x_power.h:lpc54_powerup0]`
- `[lpc546x_power.h:lpc54_powerup1]`
- `[lpc546x_power.h:lpc54_powerdown0]`
- `[lpc546x_power.h:lpc54_powerdown1]`
- `[lpc546x_power.h:lpc54_ispowered0]`
- `[lpc546x_power.h:lpc54_ispowered1]`
- `[lpc546x_power.h:lpc54_fro_powerup]`
- `[lpc546x_power.h:lpc54_ts_powerup]`
- `[lpc546x_power.h:lpc54_bodrst_powerup]`
- `[lpc546x_power.h:lpc54_bodintr_powerup]`
- `[lpc546x_power.h:lpc54_vd2ana_powerup]`
- `[lpc546x_power.h:lpc54_adc0_powerup]`
- `[lpc546x_reset.h:lpc54_reset_peripheral0]`
- `[lpc546x_reset.h:lpc54_reset_peripheral1]`
- `[lpc546x_reset.h:lpc54_reset_peripheral2]`
- `[lpc546x_reset.h:lpc54_reset_async_peripheral]`
- `[lpc546x_reset.h:lpc54_reset_flash]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[lpc54_enableclk.h:#error]` Compile-time guard: Unsupported LPC54 architecture
- `[lpc54_lcd.h:#error]` Compile-time guard: 24 BPP is only available for a TFT panel
- `[lpc54_power.h:#error]` Compile-time guard: Unsupported LPC54 architecture
- `[lpc54_reset.h:#error]` Compile-time guard: Unsupported LPC54 architecture
- `[lpc54_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc54_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc54_emc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc54_ethernet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc54_ethernet.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc54_ethernet.c:#error]` Compile-time configuration constraint: Work queue support is required in this configuration (CONFIG_SCHED_WORKQUEUE)
- `[lpc54_gpioirq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc54_i2c_master.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[lpc546x_enableclk.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[lpc546x_enableclk.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[lpc546x_power.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[lpc546x_power.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[lpc54_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc54_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc54_clrpend.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc54_dma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc54_dma.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[lpc54_dma.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc54_dma.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[lpc54_dma.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
