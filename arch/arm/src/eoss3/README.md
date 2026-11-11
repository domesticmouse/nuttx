# eoss3 (`nuttx/arch/arm/src/eoss3`)

## Overview
Hardware abstraction and architecture package for `eoss3` (EOS S3 Configuration Options; EOS S3 Peripheral Support) under `nuttx/arch/arm/src/eoss3`, providing 6 header file(s) and 8 source file(s) (including `chip.h`, `eoss3.h`, `eoss3_clockconfig.h`, `eoss3_gpio.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/eoss3/hardware`, providing 5 header file(s) and 0 source file(s) (including `eoss3_clock.h`, `eoss3_intr.h`, `eoss3_iomux.h`, `eoss3_memorymap.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[eoss3_clockconfig.h:eoss3_clockconfig]`
- `[eoss3_gpio.h:eoss3_gpioirqinitialize]`
- `[eoss3_gpio.h:eoss3_configgpio]`
- `[eoss3_gpio.h:eoss3_unconfiggpio]`
- `[eoss3_gpio.h:eoss3_gpiowrite]`
- `[eoss3_gpio.h:eoss3_gpioread]`
- `[eoss3_gpio.h:eoss3_gpioirq]`
- `[eoss3_gpio.h:eoss3_gpioirqenable]`
- `[eoss3_gpio.h:eoss3_gpioirqdisable]`
- `[eoss3_gpio.h:eoss3_gpioirqclear]`
- `[eoss3_gpio.h:eoss3_dumpgpio]`
- `[eoss3_gpio.h:gpio_pinset_t]`
- `[eoss3_gpio.h:GPIO_PIN_SHIFT]`
- `[eoss3_gpio.h:GPIO_PIN_MASK]`
- `[eoss3_gpio.h:GPIO_PIN0]`
- `[eoss3_gpio.h:GPIO_PIN1]`
- `[eoss3_gpio.h:GPIO_PIN2]`
- `[eoss3_gpio.h:GPIO_PIN3]`
- `[eoss3_gpio.h:GPIO_PIN4]`
- `[eoss3_gpio.h:GPIO_PIN5]`
- `[eoss3_gpio.h:GPIO_PIN6]`
- `[eoss3_gpio.h:GPIO_PIN7]`
- `[eoss3_gpio.h:GPIO_PIN8]`
- `[eoss3_gpio.h:GPIO_PIN9]`
- `[eoss3_lowputc.h:eoss3_lowsetup]`
- `[eoss3_start.h:eoss3_boardinitialize]`
- `[eoss3_clockconfig.c:eoss3_clockconfig]`
- `[eoss3_gpio.c:eoss3_configgpio]`
- `[eoss3_gpio.c:eoss3_unconfiggpio]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[eoss3_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[eoss3_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[eoss3_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[eoss3_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[eoss3_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[eoss3_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[eoss3_timerisr.c:#error]` Compile-time configuration constraint: SYSTICK_RELOAD exceeds the range of the RELOAD register

## Side Effects
- `[eoss3_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[eoss3_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[eoss3_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[eoss3_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[eoss3_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[eoss3_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[eoss3_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[eoss3_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[eoss3_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[eoss3_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[eoss3_lowputc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[eoss3_lowputc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
