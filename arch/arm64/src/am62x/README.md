# am62x (`nuttx/arch/arm64/src/am62x`)

## Overview
Hardware abstraction and architecture package for `am62x` (AM62x peripheral support) under `nuttx/arch/arm64/src/am62x`, providing 6 header file(s) and 5 source file(s) (including `am62x_boot.h`, `am62x_gpio.h`, `am62x_i2c.h`, `am62x_serial.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm64/src/am62x/hardware`, providing 6 header file(s) and 0 source file(s) (including `am62x_gpio.h`, `am62x_i2c.h`, `am62x_memorymap.h`, `am62x_secure_proxy.h`).

## Interface
- `[am62x_boot.h:am62x_board_initialize]`
- `[am62x_boot.h:am62x_memory_initialize]`
- `[am62x_gpio.h:am62x_gpio_initialize]`
- `[am62x_gpio.h:am62x_configgpio]`
- `[am62x_gpio.h:am62x_gpiowrite]`
- `[am62x_gpio.h:am62x_gpioread]`
- `[am62x_gpio.h:am62x_gpiooutread]`
- `[am62x_gpio.h:am62x_gpio_irq_attach]`
- `[am62x_gpio.h:am62x_gpio_irq_detach]`
- `[am62x_gpio.h:am62x_pinmux_configure]`
- `[am62x_gpio.h:gpio_pinset_t]`
- `[am62x_gpio.h:AM62X_GPIO_LINE_SHIFT]`
- `[am62x_gpio.h:AM62X_GPIO_LINE_MASK]`
- `[am62x_gpio.h:AM62X_GPIO_BANK_SHIFT]`
- `[am62x_gpio.h:AM62X_GPIO_BANK_MASK]`
- `[am62x_gpio.h:AM62X_GPIO_INPUT]`
- `[am62x_gpio.h:AM62X_GPIO_OUTPUT_ONE]`
- `[am62x_gpio.h:AM62X_GPIO_PULL_SHIFT]`
- `[am62x_gpio.h:AM62X_GPIO_PULL_MASK]`
- `[am62x_gpio.h:AM62X_GPIO_PULL_NONE]`
- `[am62x_gpio.h:AM62X_GPIO_PULL_UP]`
- `[am62x_gpio.h:AM62X_GPIO_PULL_DOWN]`
- `[am62x_gpio.h:AM62X_GPIO_IRQ_SHIFT]`
- `[am62x_i2c.h:am62x_i2cbus_initialize]`
- `[am62x_i2c.h:am62x_i2cbus_uninitialize]`
- `[am62x_serial.h:arm64_earlyserialinit]`
- `[am62x_serial.h:arm64_serialinit]`
- `[am62x_tisci.h:am62x_tisci_initialize]`
- `[am62x_tisci.h:am62x_tisci_get_version]`
- `[am62x_tisci.h:am62x_tisci_set_device_state]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[am62x_gpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[am62x_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[am62x_16550serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[am62x_16550serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[am62x_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[am62x_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[am62x_gpio.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[am62x_gpio.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[am62x_i2c.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[am62x_i2c.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[am62x_i2c.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[am62x_i2c.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[am62x_i2c.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[am62x_i2c.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
