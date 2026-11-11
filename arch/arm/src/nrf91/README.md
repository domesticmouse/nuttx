# nrf91 (`nuttx/arch/arm/src/nrf91`)

## Overview
Hardware abstraction and architecture package for `nrf91` (nRF91 Configuration Options; nRF91 Peripheral Selection) under `nuttx/arch/arm/src/nrf91`, providing 22 header file(s) and 28 source file(s) (including `chip.h`, `nrf91_clockconfig.h`, `nrf91_config.h`, `nrf91_errata.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/nrf91/hardware`, providing 18 header file(s) and 0 source file(s) (including `nrf91_clock.h`, `nrf91_ficr.h`, `nrf91_gpio.h`, `nrf91_gpiote.h`).

## Interface
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[nrf91_clockconfig.h:nrf91_clockconfig]`
- `[nrf91_clockconfig.h:NRF91_SYSTEM_CLOCK]`
- `[nrf91_clockconfig.h:NRF91_RTC_CLOCK]`
- `[nrf91_config.h:HAVE_UART0]`
- `[nrf91_config.h:HAVE_UART1]`
- `[nrf91_config.h:HAVE_UART_DEVICE]`
- `[nrf91_config.h:HAVE_UART_CONSOLE]`
- `[nrf91_errata.h:nrf91_errata_secure]`
- `[nrf91_errata.h:nrf91_ficr_ram_copy]`
- `[nrf91_gpio.h:nrf91_gpio_config]`
- `[nrf91_gpio.h:nrf91_gpio_unconfig]`
- `[nrf91_gpio.h:nrf91_gpio_write]`
- `[nrf91_gpio.h:nrf91_gpio_read]`
- `[nrf91_gpio.h:nrf91_gpio_dump]`
- `[nrf91_gpio.h:nrf91_gpio_detectmode_e]`
- `[nrf91_gpio.h:nrf91_pinset_t]`
- `[nrf91_gpio.h:GPIO_FUNC_SHIFT]`
- `[nrf91_gpio.h:GPIO_FUNC_MASK]`
- `[nrf91_gpio.h:GPIO_INPUT]`
- `[nrf91_gpio.h:GPIO_OUTPUT]`
- `[nrf91_gpio.h:GPIO_SENSE_SHIFT]`
- `[nrf91_gpio.h:GPIO_SENSE_MASK]`
- `[nrf91_gpio.h:GPIO_SENSE_NONE]`
- `[nrf91_gpio.h:GPIO_SENSE_HIGH]`
- `[nrf91_gpio.h:GPIO_SENSE_LOW]`
- `[nrf91_gpio.h:GPIO_DRIVE_SHIFT]`
- `[nrf91_gpio.h:GPIO_DRIVE_MASK]`
- `[nrf91_gpio.h:GPIO_DRIVE_S0S1]`
- `[nrf91_gpiote.h:nrf91_gpiote_set_ch_event]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[nrf91_modem.h:#error]` Compile-time guard: SHMEM base address must be word-aligned (4 bytes)
- `[nrf91_pwm.h:#error]` Compile-time guard: CONFIG_NRF91_PWM0_CHANNEL must be provided
- `[nrf91_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf91_gpio.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[nrf91_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[nrf91_gpiote.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf91_gpiote.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[nrf91_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf91_i2c.c:#error]` Compile-time configuration constraint: not implemented
- `[nrf91_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[nrf91_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[nrf91_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[nrf91_rtc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[nrf91_rtc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[nrf91_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf91_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf91_errata.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf91_errata.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf91_flash.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf91_flash.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf91_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[nrf91_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[nrf91_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[nrf91_gpiote.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
