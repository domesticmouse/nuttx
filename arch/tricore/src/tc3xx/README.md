# tc3xx (`nuttx/arch/tricore/src/tc3xx`)

## Overview
Hardware abstraction and architecture package for `tc3xx` (TC3XX Configuration Options; TC3XX Peripheral Support) under `nuttx/arch/tricore/src/tc3xx`, providing 1 header file(s) and 2 source file(s) (including `chip.h`, `tc3xx_serial.c`, `tc3xx_timerisr.c`).

## Interface
- `[chip.h:UART_PIN_RX]`
- `[chip.h:UART_PIN_TX]`
- `[tc3xx_serial.c:tricore_lowputc]`
- `[tc3xx_serial.c:tricore_earlyserialinit]`
- `[tc3xx_serial.c:tricore_serialinit]`
- `[tc3xx_serial.c:up_putc]`
- `[tc3xx_timerisr.c:up_timer_initialize]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_TC39X]`
- `[Kconfig:CONFIG_CPU_CLOCK_FREQUENCY]`
- `[Kconfig:CONFIG_TC3XX_UART0]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- `[tc3xx_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[tc3xx_serial.c:#error]` Compile-time configuration constraint: I'm confused... Do we have a serial console or not?
- `[tc3xx_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[tc3xx_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[tc3xx_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[tc3xx_serial.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
