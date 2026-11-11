# nuc1xx (`nuttx/arch/arm/src/nuc1xx`)

## Overview
Hardware abstraction and architecture package for `nuc1xx` (NUC100/120 Configuration Options; NUC1XX Peripheral Support) under `nuttx/arch/arm/src/nuc1xx`, providing 9 header file(s) and 10 source file(s) (including `chip.h`, `nuc_clockconfig.h`, `nuc_config.h`, `nuc_gpio.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/nuc1xx/hardware`, providing 19 header file(s) and 0 source file(s) (including `nuc_adc.h`, `nuc_clk.h`, `nuc_cmp.h`, `nuc_config.h`).

## Interface
- `[chip.h:ARMV6M_PERIPHERAL_INTERRUPTS]`
- `[nuc_clockconfig.h:nuc_clockconfig]`
- `[nuc_config.h:HAVE_UART]`
- `[nuc_config.h:HAVE_SERIAL_CONSOLE]`
- `[nuc_gpio.h:nuc_configgpio]`
- `[nuc_gpio.h:nuc_gpiowrite]`
- `[nuc_gpio.h:nuc_gpioread]`
- `[nuc_gpio.h:nuc_dumpgpio]`
- `[nuc_gpio.h:gpio_cfgset_t]`
- `[nuc_gpio.h:GPIO_MODE_SHIFT]`
- `[nuc_gpio.h:GPIO_MODE_MASK]`
- `[nuc_gpio.h:GPIO_INPUT]`
- `[nuc_gpio.h:GPIO_OUTPUT]`
- `[nuc_gpio.h:GPIO_OPENDRAIN]`
- `[nuc_gpio.h:GPIO_BIDI]`
- `[nuc_gpio.h:GPIO_ANALOG]`
- `[nuc_gpio.h:GPIO_DEBOUNCE]`
- `[nuc_gpio.h:GPIO_INTERRUPT_SHIFT]`
- `[nuc_gpio.h:GPIO_INTERRUPT_MASK]`
- `[nuc_gpio.h:GPIO_INTERRUPT_NONE]`
- `[nuc_gpio.h:GPIO_INTERRUPT_RISING_EDGE]`
- `[nuc_lowputc.h:nuc_lowsetup]`
- `[nuc_lowputc.h:nuc_setbaud]`
- `[nuc_lowputc.h:nuc_lowputc]`
- `[nuc_start.h:nuc_boardinitialize]`
- `[nuc_userspace.h:nuc_userspace]`
- `[nuc_clockconfig.c:nuc_clockconfig]`
- `[nuc_dumpgpio.c:nuc_dumpgpio]`
- `[nuc_gpio.c:nuc_configgpio]`
- `[nuc_gpio.c:nuc_gpiowrite]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[nuc_dumpgpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nuc_dumpgpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[nuc_dumpgpio.c:#error]` Compile-time configuration constraint: Additional support required for this number of GPIOs
- `[nuc_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nuc_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[nuc_idle.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[nuc_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nuc_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[nuc_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[nuc_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[nuc_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nuc_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[nuc_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nuc_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nuc_dumpgpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nuc_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nuc_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nuc_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[nuc_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nuc_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[nuc_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nuc_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[nuc_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[nuc_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
