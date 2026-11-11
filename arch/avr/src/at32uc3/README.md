# at32uc3 (`nuttx/arch/avr/src/at32uc3`)

## Overview
Hardware abstraction and architecture package for `at32uc3` (AT32U3 Configuration Options; AT32U3 Peripheral Selections) under `nuttx/arch/avr/src/at32uc3`, providing 27 header file(s) and 8 source file(s) (including `at32uc3.h`, `at32uc3_abdac.h`, `at32uc3_adc.h`, `at32uc3_config.h`).

## Interface
- `[at32uc3.h:up_clkinitialize]`
- `[at32uc3.h:usart_reset]`
- `[at32uc3.h:usart_configure]`
- `[at32uc3.h:up_consoleinit]`
- `[at32uc3.h:at32uc3_boardinitialize]`
- `[at32uc3.h:at32uc3_configgpio]`
- `[at32uc3.h:at32uc3_gpiowrite]`
- `[at32uc3.h:at32uc3_gpioread]`
- `[at32uc3.h:gpio_irqinitialize]`
- `[at32uc3.h:gpio_irqattach]`
- `[at32uc3.h:gpio_irqenable]`
- `[at32uc3.h:gpio_irqdisable]`
- `[at32uc3.h:GPIO_GLITCH]`
- `[at32uc3.h:GPIO_INTMODE_SHIFT]`
- `[at32uc3.h:GPIO_INTMODE_MASK]`
- `[at32uc3.h:GPIO_INTMODE_BOTH]`
- `[at32uc3.h:GPIO_INTMODE_RISING]`
- `[at32uc3.h:GPIO_INTMODE_FALLING]`
- `[at32uc3.h:GPIO_IMR0]`
- `[at32uc3.h:GPIO_IMR1]`
- `[at32uc3.h:GPIO_INTR]`
- `[at32uc3.h:GPIO_PULLUP]`
- `[at32uc3.h:GPIO_VALUE]`
- `[at32uc3.h:GPIO_HIGH]`
- `[at32uc3_abdac.h:AVR32_ABDAC_SDR_OFFSET]`
- `[at32uc3_abdac.h:AVR32_ABDAC_CR_OFFSET]`
- `[at32uc3_abdac.h:AVR32_ABDAC_IMR_OFFSET]`
- `[at32uc3_abdac.h:AVR32_ABDAC_IER_OFFSET]`
- `[at32uc3_abdac.h:AVR32_ABDAC_IDR_OFFSET]`
- `[at32uc3_abdac.h:AVR32_ABDAC_ICR_OFFSET]`

## Invariants
- `[at32uc3_pinmux.h:#error]` Compile-time guard: Unknown AVR32 chip
- `[at32uc3_pm.h:#error]` Compile-time guard: Unknown AVR32 chip
- `[chip.h:#error]` Compile-time guard: Unsupported AVR32 chip
- `[at32uc3_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[at32uc3_gpioirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[at32uc3_gpioirq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[at32uc3_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[at32uc3_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[at32uc3_lowconsole.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[at32uc3_lowconsole.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[at32uc3_lowconsole.c:#error]` Compile-time configuration constraint: No CONFIG_USARTn_SERIAL_CONSOLE Setting
- `[at32uc3_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[at32uc3_clkinit.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[at32uc3_clkinit.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[at32uc3_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[at32uc3_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[at32uc3_gpioirq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[at32uc3_gpioirq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[at32uc3_gpioirq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[at32uc3_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[at32uc3_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[at32uc3_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[at32uc3_lowconsole.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[at32uc3_lowconsole.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
