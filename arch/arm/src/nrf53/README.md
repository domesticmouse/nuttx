# nrf53 (`nuttx/arch/arm/src/nrf53`)

## Overview
Hardware abstraction and architecture package for `nrf53` (nRF53 Configuration Options; nRF53 Peripheral Selection) under `nuttx/arch/arm/src/nrf53`, providing 33 header file(s) and 37 source file(s) (including `chip.h`, `nrf53_adc.h`, `nrf53_clockconfig.h`, `nrf53_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/nrf53/hardware`, providing 37 header file(s) and 0 source file(s) (including `nrf53_cache.h`, `nrf53_clock.h`, `nrf53_ctrlap.h`, `nrf53_dppi.h`).
- `sdc`: [./sdc/README.md](./sdc/README.md) - This directory holds stub files for building Nordic SoftDevice Controller without having to pull NRFX and CMSIS just to have a few definitions. Provides 2 header(s) and 0 source file(s) (`nrf.h`, `nrf_peripherals.h`) under `nuttx/arch/arm/src/nrf53/sdc`.

## Interface
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[nrf53_adc.h:nrf53_adcinitialize]`
- `[nrf53_adc.h:nrf53_adc_ain_e]`
- `[nrf53_adc.h:nrf53_adc_res_e]`
- `[nrf53_adc.h:nrf53_adc_gain_e]`
- `[nrf53_adc.h:nrf53_adc_refsel_e]`
- `[nrf53_adc.h:nrf53_adc_tacq_e]`
- `[nrf53_adc.h:nrf53_adc_mode_e]`
- `[nrf53_adc.h:nrf53_adc_burst_e]`
- `[nrf53_adc.h:nrf53_adc_channel_s]`
- `[nrf53_clockconfig.h:nrf53_clockconfig]`
- `[nrf53_clockconfig.h:NRF53_SYSTEM_CLOCK]`
- `[nrf53_clockconfig.h:NRF53_RTC_CLOCK]`
- `[nrf53_clockconfig.h:NRF53_PCLK192M_FREQ]`
- `[nrf53_config.h:HAVE_UART0]`
- `[nrf53_config.h:HAVE_UART1]`
- `[nrf53_config.h:HAVE_UART_DEVICE]`
- `[nrf53_config.h:HAVE_UART_CONSOLE]`
- `[nrf53_cpunet.h:nrf53_board_gpio_cpunet_allow]`
- `[nrf53_cpunet.h:nrf53_cpunet_power]`
- `[nrf53_cpunet.h:nrf53_cpunet_boot]`
- `[nrf53_gpio.h:nrf53_gpio_config]`
- `[nrf53_gpio.h:nrf53_gpio_unconfig]`
- `[nrf53_gpio.h:nrf53_gpio_write]`
- `[nrf53_gpio.h:nrf53_gpio_read]`
- `[nrf53_gpio.h:nrf53_gpio_dump]`
- `[nrf53_gpio.h:nrf53_gpio_cpunet_allow]`
- `[nrf53_gpio.h:nrf53_gpio_cpunet_allow_all]`
- `[nrf53_gpio.h:nrf53_gpio_detectmode_e]`
- `[nrf53_gpio.h:nrf53_pinset_t]`
- [./hardware/README.md](./hardware/README.md)
- [./sdc/README.md](./sdc/README.md)

## Invariants
- `[nrf53_clockconfig.h:#error]` Compile-time guard: Invalid configuration
- `[nrf53_pwm.h:#error]` Compile-time guard: CONFIG_NRF53_PWM0_CHANNEL must be provided
- `[nrf53_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf53_adc.c:#error]` Compile-time configuration constraint: SAADC trigger not selected
- `[nrf53_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf53_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[nrf53_gpiote.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf53_gpiote.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[nrf53_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf53_i2c.c:#error]` Compile-time configuration constraint: not implemented
- `[nrf53_ieee802154.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf53_ieee802154.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[nrf53_rtc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[nrf53_rtc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[nrf53_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf53_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf53_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[nrf53_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[nrf53_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf53_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf53_cpunet.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf53_flash.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf53_flash.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf53_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
