# m9s12 (`nuttx/arch/hc/src/m9s12`)

## Overview
Hardware abstraction and architecture package for `m9s12` (M9S12 Configuration Options; M9S12 Peripheral Selection) under `nuttx/arch/hc/src/m9s12`, providing 16 header file(s) and 9 source file(s) (including `chip.h`, `m9s12.h`, `m9s12_atd.h`, `m9s12_crg.h`).

## Interface
- `[chip.h:HCS12_REG_BASE]`
- `[chip.h:HCS12_EEPROM_BASE]`
- `[chip.h:HCS12_SRAM_BASE]`
- `[chip.h:HCS12_FFLASH1_BASE]`
- `[chip.h:HCS12_PPAGE_BASE]`
- `[chip.h:HCS12_FFLASH2_BASE]`
- `[chip.h:HCS12_CORE1_BASE]`
- `[chip.h:HCS12_DEVID_BASE]`
- `[chip.h:HCS12_CORE2_BASE]`
- `[chip.h:HCS12_CORE3_BASE]`
- `[chip.h:HCS12_CORE4_BASE]`
- `[chip.h:HCS12_CRG_BASE]`
- `[m9s12.h:hcs12_gpioirqinitialize]`
- `[m9s12.h:hcs12_configgpio]`
- `[m9s12.h:hcs12_gpiowrite]`
- `[m9s12.h:hcs12_gpioread]`
- `[m9s12.h:hcs12_gpioirqenable]`
- `[m9s12.h:hcs12_gpioirqdisable]`
- `[m9s12.h:hcs12_dumpgpio]`
- `[m9s12.h:hcs12_ethinitialize]`
- `[m9s12.h:hcs12_spibus_initialize]`
- `[m9s12.h:hcs12_spiselect]`
- `[m9s12.h:hcs12_spistatus]`
- `[m9s12.h:GPIO_INT_SHIFT]`
- `[m9s12.h:GPIO_INT_MASK]`
- `[m9s12.h:GPIO_INT_POLARITY]`
- `[m9s12.h:GPIO_INT_ENABLE]`
- `[m9s12.h:GPIO_INT_FALLING]`
- `[m9s12.h:GPIO_INT_RISING]`
- `[m9s12.h:GPIO_OPENDRAIN]`

## Invariants
- `[m9s12_serial.h:#error]` Compile-time guard: CONFIG_SCI0_PARITY value not recognized
- `[m9s12_dumpgpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[m9s12_ethernet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[m9s12_ethernet.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[m9s12_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[m9s12_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[m9s12_gpioirq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[m9s12_registerdump.c:#error]` Compile-time configuration constraint: Need to save more registers
- `[m9s12_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[m9s12_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[m9s12_serial.c:#error]` Compile-time configuration constraint: No valid TTY devices
- `[m9s12_timerisr.c:#error]` Compile-time configuration constraint: Cannot generate CLK_TCK from HCSCLK_OSCCLK

## Side Effects
- `[m9s12_ethernet.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[m9s12_ethernet.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[m9s12_ethernet.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[m9s12_gpio.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[m9s12_gpioirq.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[m9s12_gpioirq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[m9s12_serial.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[m9s12_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[m9s12_timerisr.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[m9s12_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[m9s12_timerisr.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
