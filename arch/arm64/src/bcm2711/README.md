# bcm2711 (`nuttx/arch/arm64/src/bcm2711`)

## Overview
Hardware abstraction and architecture package for `bcm2711` (BCM2711 configuration options; Broadcom BCM2711 Peripheral Selection) under `nuttx/arch/arm64/src/bcm2711`, providing 11 header file(s) and 12 source file(s) (including `bcm2711_boot.h`, `bcm2711_cpustart.h`, `bcm2711_gpio.h`, `bcm2711_i2c.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm64/src/bcm2711/hardware`, providing 15 header file(s) and 0 source file(s) (including `bcm2711_armtimer.h`, `bcm2711_aux.h`, `bcm2711_bsc.h`, `bcm2711_dma.h`).

## Interface
- `[bcm2711_boot.h:bcm2711_board_initialize]`
- `[bcm2711_cpustart.h:bcm2711_cpustart]`
- `[bcm2711_gpio.h:bcm2711_gpio_set_pulls]`
- `[bcm2711_gpio.h:bcm2711_gpio_set_func]`
- `[bcm2711_gpio.h:bcm2711_gpio_pin_set]`
- `[bcm2711_gpio.h:bcm2711_gpio_pin_get]`
- `[bcm2711_gpio.h:bcm2711_gpio_event_get]`
- `[bcm2711_gpio.h:bcm2711_gpio_event_clear]`
- `[bcm2711_gpio.h:bcm2711_gpio_rising_edge]`
- `[bcm2711_gpio.h:bcm2711_gpio_falling_edge]`
- `[bcm2711_gpio.h:bcm2711_gpio_high_level]`
- `[bcm2711_gpio.h:bcm2711_gpio_low_level]`
- `[bcm2711_gpio.h:bcm2711_gpio_rising_edge_async]`
- `[bcm2711_gpio.h:bcm2711_gpio_falling_edge_async]`
- `[bcm2711_gpio.h:bcm2711_gpio_irq_attach]`
- `[bcm2711_gpio.h:bcm2711_gpio_irq_detach]`
- `[bcm2711_gpio.h:bcm2711_gpio_func_e]`
- `[bcm2711_i2c.h:bcm2711_i2cbus_initialize]`
- `[bcm2711_i2c.h:bcm2711_i2cbus_uninitialize]`
- `[bcm2711_mailbox.h:bcm2711_mbox_getcputemp]`
- `[bcm2711_mailbox.h:bcm2711_mbox_getrev]`
- `[bcm2711_mailbox.h:bcm2711_mbox_getmodel]`
- `[bcm2711_mailbox.h:bcm2711_mbox_getmac]`
- `[bcm2711_mailbox.h:bcm2711_mbox_getpwr]`
- `[bcm2711_mailbox.h:bcm2711_mbox_setpwr]`
- `[bcm2711_mailbox.h:bcm2711_mbox_ledset]`
- `[bcm2711_mailbox.h:bcm2711_mbox_getclken]`
- `[bcm2711_mailbox.h:bcm2711_mbox_setclken]`
- `[bcm2711_mailbox.h:bcm2711_mbox_getclkrate]`
- `[bcm2711_mailbox.h:bcm2711_mbox_setclkrate]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[bcm2711_fb.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bcm2711_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bcm2711_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bcm2711_i2c.c:#error]` Compile-time configuration constraint: BCM2711 datasheet does not declare the alternate function needed for this pin pair.
- `[bcm2711_mailbox.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bcm2711_oneshot.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[bcm2711_pwm.c:#error]` Compile-time configuration constraint: Invalid pin selection for PWM0 channel 1!
- `[bcm2711_sdio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bcm2711_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bcm2711_spi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bcm2711_spi.c:#error]` Compile-time configuration constraint: Invalid GPIO number for SPI0 CE0

## Side Effects
- `[bcm2711_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[bcm2711_gpio.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[bcm2711_gpio.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[bcm2711_i2c.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[bcm2711_i2c.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[bcm2711_i2c.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[bcm2711_i2c.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[bcm2711_i2c.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[bcm2711_lowputc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[bcm2711_lowputc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[bcm2711_mailbox.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[bcm2711_mailbox.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
