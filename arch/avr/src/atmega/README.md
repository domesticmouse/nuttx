# atmega (`nuttx/arch/avr/src/atmega`)

## Overview
Hardware abstraction and architecture package for `atmega` (ATMega Configuration Options; ATMega Peripheral Selections) under `nuttx/arch/avr/src/atmega`, providing 4 header file(s) and 4 source file(s) (including `atmega.h`, `atmega_config.h`, `atmega_memorymap.h`, `chip.h`).

## Interface
- `[atmega.h:up_clkinitialize]`
- `[atmega.h:usart0_reset]`
- `[atmega.h:usart1_reset]`
- `[atmega.h:usart0_configure]`
- `[atmega.h:usart1_configure]`
- `[atmega.h:up_consoleinit]`
- `[atmega.h:atmega_boardinitialize]`
- `[atmega.h:gpio_irqinitialize]`
- `[atmega.h:gpio_irqattach]`
- `[atmega.h:gpio_irqenable]`
- `[atmega.h:gpio_irqdisable]`
- `[atmega_config.h:HAVE_USART_DEVICE]`
- `[atmega_config.h:HAVE_SERIAL_CONSOLE]`
- `[atmega_config.h:USE_SERIALDRIVER]`
- `[atmega_config.h:USE_EARLYSERIALINIT]`
- `[atmega_lowconsole.c:usart0_reset]`
- `[atmega_lowconsole.c:usart1_reset]`
- `[atmega_lowconsole.c:usart0_configure]`
- `[atmega_lowconsole.c:usart1_configure]`
- `[atmega_lowconsole.c:up_consoleinit]`
- `[atmega_lowconsole.c:avr_lowputc]`
- `[atmega_lowinit.c:avr_lowinit]`
- `[atmega_serial.c:avr_earlyserialinit]`
- `[atmega_serial.c:avr_serialinit]`
- `[atmega_serial.c:up_putc]`
- `[atmega_timerisr.c:up_timer_initialize]`
- `[Kconfig:CONFIG_ARCH_CHIP_ATMEGA128]`
- `[Kconfig:CONFIG_ARCH_CHIP_ATMEGA1284P]`
- `[Kconfig:CONFIG_ARCH_CHIP_ATMEGA2560]`
- `[Kconfig:CONFIG_AVR_USART0]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported AVR chip
- `[atmega_lowconsole.c:#error]` Compile-time configuration constraint: Unsupported word size
- `[atmega_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[atmega_timerisr.c:#error]` Compile-time configuration constraint: Cannot represent this timer frequency

## Side Effects
- `[atmega_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[atmega_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[atmega_timerisr.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
