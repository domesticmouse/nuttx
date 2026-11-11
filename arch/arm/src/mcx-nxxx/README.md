# mcx-nxxx (`nuttx/arch/arm/src/mcx-nxxx`)

## Overview
Hardware abstraction and architecture package for `mcx-nxxx` (MCX NXXx Chip Selection; NXXX Peripheral Selection) under `nuttx/arch/arm/src/mcx-nxxx`, providing 7 header file(s) and 12 source file(s) (including `chip.h`, `nxxx_clockconfig.h`, `nxxx_gpio.h`, `nxxx_lowputc.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/mcx-nxxx/hardware`, providing 13 header file(s) and 0 source file(s) (including `nxxx_clock.h`, `nxxx_flexcomm.h`, `nxxx_fmu.h`, `nxxx_gdet.h`).

## Interface
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[nxxx_clockconfig.h:nxxx_clockconfig]`
- `[nxxx_clockconfig.h:nxxx_set_periphclock]`
- `[nxxx_clockconfig.h:nxxx_set_clock_gate]`
- `[nxxx_clockconfig.h:nxxx_get_coreclk]`
- `[nxxx_gpio.h:nxxx_gpioirq_initialize]`
- `[nxxx_gpio.h:nxxx_config_gpio]`
- `[nxxx_gpio.h:nxxx_gpio_write]`
- `[nxxx_gpio.h:nxxx_gpio_read]`
- `[nxxx_gpio.h:nxxx_gpioirq_attach]`
- `[nxxx_gpio.h:nxxx_gpioirq_configure]`
- `[nxxx_gpio.h:nxxx_gpioirq_enable]`
- `[nxxx_gpio.h:nxxx_gpioirq_disable]`
- `[nxxx_gpio.h:gpio_pinset_t]`
- `[nxxx_gpio.h:GPIO_MODE_SHIFT]`
- `[nxxx_gpio.h:GPIO_MODE_MASK]`
- `[nxxx_gpio.h:GPIO_INPUT]`
- `[nxxx_gpio.h:GPIO_OUTPUT]`
- `[nxxx_gpio.h:GPIO_INTERRUPT]`
- `[nxxx_gpio.h:GPIO_OUTPUT_SHIFT]`
- `[nxxx_gpio.h:GPIO_OUTPUT_MASK]`
- `[nxxx_gpio.h:GPIO_OUTPUT_ZERO]`
- `[nxxx_gpio.h:GPIO_OUTPUT_ONE]`
- `[nxxx_gpio.h:GPIO_INTBOTHCFG_SHIFT]`
- `[nxxx_gpio.h:GPIO_INTBOTHCFG_MASK]`
- `[nxxx_gpio.h:GPIO_INTBOTH_EDGES]`
- `[nxxx_lowputc.h:nxxx_lowsetup]`
- `[nxxx_lowputc.h:nxxx_lpuart_configure]`
- `[nxxx_lowputc.h:uart_config_s]`
- `[nxxx_lpi2c.h:nxxx_i2cbus_initialize]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[nxxx_serial.h:#error]` Compile-time guard: MCX-NXXX LPUART receive or transmit DMA requires CONFIG_NXXX_EDMA
- `[nxxx_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nxxx_gpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[nxxx_gpiobase.c:#error]` Compile-time configuration constraint: Unrecognized NXXx architecture
- `[nxxx_gpioirq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[nxxx_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nxxx_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[nxxx_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[nxxx_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[nxxx_irq.c:#error]` Compile-time configuration constraint: Missing logic
- `[nxxx_lpi2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nxxx_lpi2c.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[nxxx_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nxxx_clockconfig.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[nxxx_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nxxx_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nxxx_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nxxx_gpioirq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nxxx_gpioirq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nxxx_gpioirq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[nxxx_gpioirq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[nxxx_gpioirq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[nxxx_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[nxxx_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
