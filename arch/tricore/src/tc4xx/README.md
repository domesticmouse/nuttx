# tc4xx (`nuttx/arch/tricore/src/tc4xx`)

## Overview
Hardware abstraction and architecture package for `tc4xx` (TC4XX Configuration Options; TC4XX Peripheral Support) under `nuttx/arch/tricore/src/tc4xx`, providing 1 header file(s) and 2 source file(s) (including `chip.h`, `tc4xx_serial.c`, `tc4xx_timerisr.c`).

## Interface
- `[chip.h:UART_PIN_RX]`
- `[chip.h:UART_PIN_TX]`
- `[tc4xx_serial.c:tricore_lowputc]`
- `[tc4xx_serial.c:tricore_earlyserialinit]`
- `[tc4xx_serial.c:tricore_serialinit]`
- `[tc4xx_serial.c:up_putc]`
- `[tc4xx_timerisr.c:up_timer_initialize]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_TC4DX]`
- `[Kconfig:CONFIG_CPU_CLOCK_FREQUENCY]`
- `[Kconfig:CONFIG_TC4XX_UART0]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- `[tc4xx_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[tc4xx_serial.c:#error]` Compile-time configuration constraint: I'm confused... Do we have a serial console or not?
- `[tc4xx_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[tc4xx_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[tc4xx_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[tc4xx_serial.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
