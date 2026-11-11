# cxd56xx (`nuttx/arch/arm/src/cxd56xx`)

## Overview
Hardware abstraction and architecture package for `cxd56xx` (CXD56xx Options; CXD56xx Package Configuration) under `nuttx/arch/arm/src/cxd56xx`, providing 44 header file(s) and 58 source file(s) (including `chip.h`, `cxd56_adc.h`, `cxd56_charger.h`, `cxd56_clock.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/cxd56xx/hardware`, providing 23 header file(s) and 0 source file(s) (including `cxd5602_backupmem.h`, `cxd5602_isop.h`, `cxd5602_isop_hadc0_highspeed.h`, `cxd5602_memorymap.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[cxd56_adc.h:cxd56_adc_getinterval]`
- `[cxd56_charger.h:cxd56_charger_initialize]`
- `[cxd56_charger.h:cxd56_charger_uninitialize]`
- `[cxd56_clock.h:cxd56_spif_clock_enable]`
- `[cxd56_clock.h:cxd56_spif_clock_disable]`
- `[cxd56_clock.h:cxd56_get_cpu_baseclk]`
- `[cxd56_clock.h:cxd56_cpu_clock_enable]`
- `[cxd56_clock.h:cxd56_cpulist_clock_enable]`
- `[cxd56_clock.h:cxd56_cpu_clock_disable]`
- `[cxd56_clock.h:cxd56_cpulist_clock_disable]`
- `[cxd56_clock.h:cxd56_cpu_reset]`
- `[cxd56_clock.h:cxd56_cpulist_reset]`
- `[cxd56_clock.h:cxd56_usb_clock_enable]`
- `[cxd56_clock.h:cxd56_usb_clock_disable]`
- `[cxd56_clock.h:cxd56_emmc_clock_enable]`
- `[cxd56_clock.h:cxd56_emmc_clock_disable]`
- `[cxd56_clock.h:cxd56_sdio_clock_enable]`
- `[cxd56_clock.h:cxd56_sdio_clock_disable]`
- `[cxd56_clock.h:cxd56_audio_clock_enable]`
- `[cxd56_clock.h:cxd56_audio_clock_disable]`
- `[cxd56_clock.h:cxd56_audio_clock_is_enabled]`
- `[cxd56_clock.h:cxd56_spi_clock_enable]`
- `[cxd56_clock.h:cxd56_spi_clock_disable]`
- `[cxd56_clock.h:cxd56_spi_clock_gate_enable]`
- `[cxd56_clock.h:cxd56_spi_clock_gate_disable]`
- `[cxd56_clock.h:cxd56_spi_clock_gear_adjust]`
- `[cxd56_clock.h:cxd56_i2c_clock_enable]`
- `[cxd56_clock.h:cxd56_i2c_clock_disable]`
- `[cxd56_clock.h:cxd56_i2c_clock_gate_enable]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[cxd56_cpu1signal.h:#error]` Compile-time guard: CXD56_CPU1_DEV must be smaller than 0xf
- `[cxd56_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[cxd56_allocateheap.c:#error]` Compile-time configuration constraint: Invalid memory configuration
- `[cxd56_backuplog.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[cxd56_backuplog.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[cxd56_charger.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[cxd56_clock.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[cxd56_clock.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[cxd56_cpufifo.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[cxd56_cpufifo.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[cxd56_dmac.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[cxd56_dmac.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[cxd56_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[cxd56_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[cxd56_cisif.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[cxd56_cisif.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[cxd56_cisif.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[cxd56_cisif.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[cxd56_cisif.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[cxd56_clock.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[cxd56_clock.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[cxd56_clock.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[cxd56_cpufifo.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[cxd56_cpufifo.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
