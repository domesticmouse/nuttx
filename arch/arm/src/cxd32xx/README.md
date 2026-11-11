# cxd32xx (`nuttx/arch/arm/src/cxd32xx`)

## Overview
Hardware abstraction and architecture package for `cxd32xx` (Peripheral Support) under `nuttx/arch/arm/src/cxd32xx`, providing 4 header file(s) and 6 source file(s) (including `chip.h`, `cxd32_config.h`, `cxd32_serial.h`, `cxd32_uart.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/cxd32xx/hardware`, providing 4 header file(s) and 0 source file(s) (including `cxd3277_clockfreq.h`, `cxd3277_memorymap.h`, `cxd32_timer.h`, `cxd32_uart.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[cxd32_config.h:HAVE_UART]`
- `[cxd32_config.h:HAVE_CONSOLE]`
- `[cxd32_uart.h:cxd32_lowsetup]`
- `[cxd32_uart.h:cxd32_uart_reset]`
- `[cxd32_uart.h:cxd32_uart_setup]`
- `[cxd32_uart.h:cxd32_setbaud]`
- `[cxd32_uart.h:cxd32_uart_initialize]`
- `[cxd32_irq.c:up_irqinitialize]`
- `[cxd32_irq.c:up_disable_irq]`
- `[cxd32_irq.c:up_enable_irq]`
- `[cxd32_irq.c:arm_ack_irq]`
- `[cxd32_irq.c:up_prioritize_irq]`
- `[cxd32_serial.c:arm_earlyserialinit]`
- `[cxd32_serial.c:arm_serialinit]`
- `[cxd32_serial.c:up_putc]`
- `[cxd32_serial_pl011.c:arm_earlyserialinit]`
- `[cxd32_serial_pl011.c:arm_serialinit]`
- `[cxd32_serial_pl011.c:pl011_platform_setup]`
- `[cxd32_serial_pl011.c:pl011_platform_shutdown]`
- `[cxd32_start.c:g_idle_topstack]`
- `[cxd32_start.c:__start]`
- `[cxd32_start.c:showprogress]`
- `[cxd32_timerisr.c:up_timer_initialize]`
- `[cxd32_timerisr.c:cxd32_timerget]`
- `[cxd32_uart.c:arm_lowputc]`
- `[cxd32_uart.c:cxd32_lowsetup]`
- `[cxd32_uart.c:cxd32_uart_reset]`
- `[cxd32_uart.c:cxd32_uart_setup]`
- `[cxd32_uart.c:cxd32_uart_initialize]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[cxd32_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[cxd32_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[cxd32_irq.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[cxd32_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[cxd32_serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[cxd32_timerisr.c:#error]` Compile-time configuration constraint: TICK_RELOAD exceeds the range of the RELOAD register
- `[cxd32_uart.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[cxd32_uart.c:#error]` Compile-time configuration constraint: No CONFIG_UARTn_SERIAL_CONSOLE Setting

## Side Effects
- `[cxd32_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[cxd32_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[cxd32_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[cxd32_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[cxd32_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[cxd32_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[cxd32_serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[cxd32_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[cxd32_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[cxd32_serial.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[cxd32_start.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[cxd32_timerisr.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
