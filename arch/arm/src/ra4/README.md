# ra4 (`nuttx/arch/arm/src/ra4`)

## Overview
Hardware abstraction and architecture package for `ra4` (RA Configuration Options; RA4M1 Peripheral Support) under `nuttx/arch/arm/src/ra4`, providing 7 header file(s) and 10 source file(s) (including `chip.h`, `ra_clockconfig.h`, `ra_gpio.h`, `ra_icu.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/ra4/hardware`, providing 15 header file(s) and 0 source file(s) (including `ra4m1_icu.h`, `ra4m1_memorymap.h`, `ra4m1_mstp.h`, `ra4m1_pinmap.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[ra_clockconfig.h:ra_clockconfig]`
- `[ra_gpio.h:ra_configgpio]`
- `[ra_gpio.h:ra_gpiowrite]`
- `[ra_gpio.h:ra_gpioread]`
- `[ra_gpio.h:gpio_pinset_t]`
- `[ra_icu.h:ra_attach_icu]`
- `[ra_icu.h:ra_clear_ir]`
- `[ra_lowputc.h:ra_lowsetup]`
- `[ra_pwm.h:ra_pwm_initialize]`
- `[ra_pwm.h:ra_pwm_uninitialize]`
- `[ra_pwm.h:ra_pwminitialize]`
- `[ra_pwm.h:ra_pwm_lowerhalf_s]`
- `[ra_start.h:ra_boardinitialize]`
- `[ra_allocateheap.c:up_allocate_heap]`
- `[ra_clockconfig.c:ra_clockconfig]`
- `[ra_gpio.c:ra_configgpio]`
- `[ra_gpio.c:ra_gpiowrite]`
- `[ra_gpio.c:ra_gpioread]`
- `[ra_icu.c:ra_attach_icu]`
- `[ra_icu.c:ra_clear_ir]`
- `[ra_irq.c:up_irqinitialize]`
- `[ra_irq.c:up_disable_irq]`
- `[ra_irq.c:up_enable_irq]`
- `[ra_irq.c:arm_ack_irq]`
- `[ra_irq.c:up_prioritize_irq]`
- `[ra_lowputc.c:arm_lowputc]`
- `[ra_lowputc.c:up_putc]`
- `[ra_lowputc.c:ra_lowsetup]`
- `[ra_pwm.c:ra_pwminitialize]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[ra_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ra_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ra_lowputc.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[ra_lowputc.c:#error]` Compile-time configuration constraint: No CONFIG_UARTn_SERIAL_CONSOLE Setting
- `[ra_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ra_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ra_timerisr.c:#error]` Compile-time configuration constraint: SYSTICK_RELOAD exceeds the range of the RELOAD register

## Side Effects
- `[ra_clockconfig.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[ra_clockconfig.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[ra_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ra_gpio.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[ra_gpio.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[ra_icu.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ra_icu.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[ra_icu.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ra_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ra_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ra_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ra_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
