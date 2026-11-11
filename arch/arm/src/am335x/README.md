# am335x (`nuttx/arch/arm/src/am335x`)

## Overview
Hardware abstraction and architecture package for `am335x` (AM335x Configuration Options; TI AM335X Peripheral Support) under `nuttx/arch/arm/src/am335x`, providing 14 header file(s) and 16 source file(s) (including `am335x_boot.h`, `am335x_can.h`, `am335x_clockconfig.h`, `am335x_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/am335x/hardware`, providing 15 header file(s) and 0 source file(s) (including `am3358_memorymap.h`, `am3358_pinmux.h`, `am335x_dcan.h`, `am335x_gpio.h`).

## Interface
- `[am335x_boot.h:am335x_memory_initialize]`
- `[am335x_boot.h:am335x_board_initialize]`
- `[am335x_can.h:am335x_can_initialize]`
- `[am335x_can.h:am335x_can_uninitialize]`
- `[am335x_clockconfig.h:am335x_clockconfig]`
- `[am335x_config.h:HAVE_UART_DEVICE]`
- `[am335x_config.h:HAVE_SERIAL_CONSOLE]`
- `[am335x_gpio.h:am335x_gpioirq_initialize]`
- `[am335x_gpio.h:am335x_gpio_config]`
- `[am335x_gpio.h:am335x_gpio_write]`
- `[am335x_gpio.h:am335x_gpio_read]`
- `[am335x_gpio.h:am335x_gpioirq]`
- `[am335x_gpio.h:am335x_gpioirq_enable]`
- `[am335x_gpio.h:am335x_gpioirq_disable]`
- `[am335x_gpio.h:am335x_dump_gpio]`
- `[am335x_gpio.h:am335x_periph_gpio]`
- `[am335x_gpio.h:gpio_pinset_t]`
- `[am335x_gpio.h:GPIO_MODE_SHIFT]`
- `[am335x_gpio.h:GPIO_MODE_MASK]`
- `[am335x_gpio.h:GPIO_INPUT]`
- `[am335x_gpio.h:GPIO_OUTPUT]`
- `[am335x_gpio.h:GPIO_PERIPH]`
- `[am335x_gpio.h:GPIO_INT_SHIFT]`
- `[am335x_gpio.h:GPIO_INT_MASK]`
- `[am335x_gpio.h:GPIO_INT_NONE]`
- `[am335x_gpio.h:GPIO_INT_RISING]`
- `[am335x_gpio.h:GPIO_INT_FALLING]`
- `[am335x_gpio.h:GPIO_INT_BOTHEDGES]`
- `[am335x_gpio.h:GPIO_INT_HIGHLEVEL]`
- `[am335x_i2c.h:am335x_i2cbus_initialize]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[am335x_boot.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[am335x_boot.c:#error]` Compile-time configuration constraint: High vector remap cannot be performed if we are using a ROM page table
- `[am335x_can.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[am335x_can.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[am335x_edid.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[am335x_gpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[am335x_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[am335x_i2c.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[am335x_i2c.c:#error]` Compile-time configuration constraint: I2C slave logic is not supported yet for AM335X
- `[am335x_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[am335x_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[am335x_lcdc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[am335x_boot.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[am335x_can.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[am335x_can.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[am335x_can.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[am335x_can.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[am335x_can.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[am335x_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[am335x_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[am335x_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[am335x_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[am335x_gpioirq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[am335x_gpioirq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)

## Verification
- Run: `make test`
