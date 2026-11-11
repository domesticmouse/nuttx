# avrdx (`nuttx/arch/avr/src/avrdx`)

## Overview
Hardware abstraction and architecture package for `avrdx` (AVR DA/DB Configuration Options; AVR DA/DB Peripheral Selections) under `nuttx/arch/avr/src/avrdx`, providing 11 header file(s) and 13 source file(s) (including `avrdx.h`, `avrdx_config.h`, `avrdx_delay_loop.h`, `avrdx_gpio.h`).

## Subdirectories & Boundaries
- `iodefs`: [./iodefs/README.md](./iodefs/README.md) - Hardware abstraction and architecture package for `iodefs` under `nuttx/arch/avr/src/avrdx/iodefs`, providing 3 header file(s) and 0 source file(s) (including `avr128da28.h`, `avr128da64.h`, `avr128db64.h`).

## Interface
- `[avrdx.h:up_clkinitialize]`
- `[avrdx.h:avrdx_current_freq_main_prescaler]`
- `[avrdx.h:avrdx_current_freq_per]`
- `[avrdx.h:avrdx_current_freq_cpu]`
- `[avrdx.h:up_consoleinit]`
- `[avrdx.h:avrdx_boardinitialize]`
- `[avrdx.h:avrdx_up_initialize]`
- `[avrdx.h:AVRDX_PORT]`
- `[avrdx.h:AVRDX_PORT_ADDR]`
- `[avrdx_config.h:AVRDX_SERIAL_CONSOLE_USART_N]`
- `[avrdx_config.h:USE_SERIALDRIVER]`
- `[avrdx_delay_loop.h:avrdx_delay_loop]`
- `[avrdx_gpio.h:avrdx_gpio_isr_mux_init]`
- `[avrdx_gpio.h:avrdx_irq_attach_gpio_mux]`
- `[avrdx_gpio.h:avrdx_irq_detach_gpio_mux]`
- `[avrdx_gpio.h:AVRDX_GPIO_PORTA_IDX]`
- `[avrdx_gpio.h:AVRDX_GPIO_PORTC_IDX]`
- `[avrdx_gpio.h:AVRDX_GPIO_PORTD_IDX]`
- `[avrdx_gpio.h:AVRDX_GPIO_PORTF_IDX]`
- `[avrdx_gpio.h:AVRDX_GPIO_PORTB_IDX]`
- `[avrdx_gpio.h:AVRDX_GPIO_PORTE_IDX]`
- `[avrdx_gpio.h:AVRDX_GPIO_PORTG_IDX]`
- `[avrdx_serial.h:avrdx_usart_reset]`
- `[avrdx_serial.h:avrdx_usart_configure]`
- `[avrdx_serial.h:avrdx_uart_priv_s]`
- `[avrdx_serial.h:AVRDX_USART]`
- `[avrdx_serial.h:AVRDX_USART_PORT]`
- `[avrdx_serial.h:AVRDX_USART_DEV_PRIV]`
- `[avrdx_swint.h:avrdx_swint_allocate]`
- `[avrdx_swint.h:avrdx_swint_raise]`
- [./iodefs/README.md](./iodefs/README.md)

## Invariants
- `[avrdx_iodefs.h:#error]` Compile-time guard: I/O register definitions for this chip are missing
- `[avrdx_swint.h:#error]` Compile-time guard: Kconfig should allow 32 vectors at most
- `[avrdx_ws2812.h:static_assert]` Enforces compile-time structure size and layout invariants
- `[chip.h:#error]` Compile-time guard: Unsupported AVR chip
- `[avrdx_gpio_isr_mux.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[avrdx_gpio_isr_mux.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[avrdx_lowconsole.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[avrdx_lowconsole.c:#error]` Compile-time configuration constraint: CONFIG_USART0_PARITY
- `[avrdx_lowinit.c:#error]` Compile-time configuration constraint: Unsupported frequency
- `[avrdx_peripherals.c:#error]` Compile-time configuration constraint: Kconfig error, no option is set
- `[avrdx_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[avrdx_serial.c:#error]` Compile-time configuration constraint: USART0 DMA is not supported

## Side Effects
- `[avrdx_gpio_isr_mux.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[avrdx_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[avrdx_swint.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[avrdx_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[avrdx_timerisr.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[avrdx_timerisr_tickless_alarm.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[avrdx_timerisr_tickless_alarm.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[avrdx_twi.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
