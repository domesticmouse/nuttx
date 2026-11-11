# nrf52 (`nuttx/arch/arm/src/nrf52`)

## Overview
Hardware abstraction and architecture package for `nrf52` (nRF52 Configuration Options; nRF52 Peripheral Selection) under `nuttx/arch/arm/src/nrf52`, providing 33 header file(s) and 39 source file(s) (including `chip.h`, `nrf52_adc.h`, `nrf52_clockconfig.h`, `nrf52_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/nrf52/hardware`, providing 25 header file(s) and 0 source file(s) (including `nrf52_clock.h`, `nrf52_ficr.h`, `nrf52_gpio.h`, `nrf52_gpiote.h`).
- `sdc`: [./sdc/README.md](./sdc/README.md) - This directory holds stub files for building Nordic SoftDevice Controller without having to pull NRFX and CMSIS just to have a few definitions. Provides 2 header(s) and 0 source file(s) (`nrf.h`, `nrf_peripherals.h`) under `nuttx/arch/arm/src/nrf52/sdc`.

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[nrf52_adc.h:nrf52_adcinitialize]`
- `[nrf52_adc.h:nrf52_adc_ain_e]`
- `[nrf52_adc.h:nrf52_adc_res_e]`
- `[nrf52_adc.h:nrf52_adc_gain_e]`
- `[nrf52_adc.h:nrf52_adc_refsel_e]`
- `[nrf52_adc.h:nrf52_adc_tacq_e]`
- `[nrf52_adc.h:nrf52_adc_mode_e]`
- `[nrf52_adc.h:nrf52_adc_burst_e]`
- `[nrf52_adc.h:nrf52_adc_channel_s]`
- `[nrf52_clockconfig.h:nrf52_clockconfig]`
- `[nrf52_clockconfig.h:NRF52_SYSTEM_CLOCK]`
- `[nrf52_clockconfig.h:NRF52_RTC_CLOCK]`
- `[nrf52_config.h:HAVE_UART0]`
- `[nrf52_config.h:HAVE_UART1]`
- `[nrf52_config.h:HAVE_UART_DEVICE]`
- `[nrf52_config.h:HAVE_UART_CONSOLE]`
- `[nrf52_gpio.h:nrf52_gpio_config]`
- `[nrf52_gpio.h:nrf52_gpio_unconfig]`
- `[nrf52_gpio.h:nrf52_gpio_write]`
- `[nrf52_gpio.h:nrf52_gpio_read]`
- `[nrf52_gpio.h:nrf52_gpio_dump]`
- `[nrf52_gpio.h:nrf52_gpio_detectmode_e]`
- `[nrf52_gpio.h:nrf52_pinset_t]`
- `[nrf52_gpio.h:GPIO_FUNC_SHIFT]`
- `[nrf52_gpio.h:GPIO_FUNC_MASK]`
- `[nrf52_gpio.h:GPIO_INPUT]`
- `[nrf52_gpio.h:GPIO_OUTPUT]`
- `[nrf52_gpio.h:GPIO_SENSE_SHIFT]`
- `[nrf52_gpio.h:GPIO_SENSE_MASK]`
- [./hardware/README.md](./hardware/README.md)
- [./sdc/README.md](./sdc/README.md)

## Invariants
- `[nrf52_pwm.h:#error]` Compile-time guard: CONFIG_NRF52_PWM0_CHANNEL must be provided
- `[nrf52_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf52_adc.c:#error]` Compile-time configuration constraint: SAADC trigger not selected
- `[nrf52_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf52_flash.c:#error]` Compile-time configuration constraint: This file requires Kconfig ALLOW_BSD_COMPONENTS
- `[nrf52_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[nrf52_gpiote.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf52_gpiote.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[nrf52_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf52_i2c.c:#error]` Compile-time configuration constraint: not implemented
- `[nrf52_i2c_bitbang.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf52_idle.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[nrf52_rtc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[nrf52_rtc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[nrf52832_errdata.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf52832_errdata.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf52_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf52_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf52_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[nrf52_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[nrf52_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf52_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf52_flash.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf52_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
