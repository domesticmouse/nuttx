# nrf54l (`nuttx/arch/arm/src/nrf54l`)

## Overview
Hardware abstraction and architecture package for `nrf54l` (nRF54L Configuration Options; nRF54L Peripheral Selection) under `nuttx/arch/arm/src/nrf54l`, providing 27 header file(s) and 32 source file(s) (including `chip.h`, `nrf54l_adc.h`, `nrf54l_clockconfig.h`, `nrf54l_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/nrf54l/hardware`, providing 23 header file(s) and 0 source file(s) (including `nrf54l_cache.h`, `nrf54l_clock.h`, `nrf54l_dppic.h`, `nrf54l_ficr.h`).
- `sdc`: [./sdc/README.md](./sdc/README.md) - Hardware abstraction and architecture package for `sdc` under `nuttx/arch/arm/src/nrf54l/sdc`, providing 2 header file(s) and 0 source file(s) (including `nrf.h`, `nrfx.h`).

## Interface
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:NRF54L_GPIO_NPORTS]`
- `[chip.h:NRF54L_GPIO_PIN_COUNTS]`
- `[nrf54l_adc.h:nrf54l_adcinitialize]`
- `[nrf54l_adc.h:nrf54l_adc_ain_e]`
- `[nrf54l_adc.h:nrf54l_adc_gain_e]`
- `[nrf54l_adc.h:nrf54l_adc_refsel_e]`
- `[nrf54l_adc.h:nrf54l_adc_tacq_e]`
- `[nrf54l_adc.h:nrf54l_adc_mode_e]`
- `[nrf54l_adc.h:nrf54l_adc_burst_e]`
- `[nrf54l_adc.h:nrf54l_adc_channel_s]`
- `[nrf54l_clockconfig.h:nrf54l_clockconfig]`
- `[nrf54l_config.h:HAVE_UART_DEVICE]`
- `[nrf54l_config.h:HAVE_UART_CONSOLE]`
- `[nrf54l_gpio.h:nrf54l_gpio_config]`
- `[nrf54l_gpio.h:nrf54l_gpio_unconfig]`
- `[nrf54l_gpio.h:nrf54l_gpio_write]`
- `[nrf54l_gpio.h:nrf54l_gpio_read]`
- `[nrf54l_gpio.h:nrf54l_gpio_detectmode]`
- `[nrf54l_gpio.h:nrf54l_gpio_detectmode_e]`
- `[nrf54l_gpio.h:nrf54l_pinset_t]`
- `[nrf54l_gpio.h:GPIO_FUNC_SHIFT]`
- `[nrf54l_gpio.h:GPIO_FUNC_MASK]`
- `[nrf54l_gpio.h:GPIO_INPUT]`
- `[nrf54l_gpio.h:GPIO_OUTPUT]`
- `[nrf54l_gpio.h:GPIO_SENSE_SHIFT]`
- `[nrf54l_gpio.h:GPIO_SENSE_MASK]`
- `[nrf54l_gpio.h:GPIO_SENSE_NONE]`
- `[nrf54l_gpio.h:GPIO_SENSE_HIGH]`
- `[nrf54l_gpio.h:GPIO_SENSE_LOW]`
- [./hardware/README.md](./hardware/README.md)
- [./sdc/README.md](./sdc/README.md)

## Invariants
- `[nrf54l_pwm.h:#error]` Compile-time guard: CONFIG_NRF54L_PWM0_CHANNEL must be provided
- `[nrf54l_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf54l_adc.c:#error]` Compile-time configuration constraint: SAADC trigger not selected
- `[nrf54l_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf54l_clockconfig.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[nrf54l_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[nrf54l_gpiote.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf54l_gpiote.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[nrf54l_grtc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf54l_grtc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[nrf54l_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf54l_i2c.c:#error]` Compile-time configuration constraint: not implemented

## Side Effects
- `[nrf54l_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf54l_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf54l_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[nrf54l_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[nrf54l_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf54l_clockconfig.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[nrf54l_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf54l_flash.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf54l_flash.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf54l_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf54l_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[nrf54l_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
