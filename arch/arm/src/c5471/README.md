# c5471 (`nuttx/arch/arm/src/c5471`)

## Overview
Hardware abstraction and architecture package for `c5471` (C5471 Configuration Options; IrDA UART Configuration) under `nuttx/arch/arm/src/c5471`, providing 1 header file(s) and 5 source file(s) (including `chip.h`, `c5471_ethernet.c`, `c5471_irq.c`, `c5471_serial.c`).

## Interface
- `[chip.h:EIM_RAM_START]`
- `[chip.h:EIM_CTRL]`
- `[chip.h:EIM_STATUS]`
- `[chip.h:EIM_CPU_TXBA]`
- `[chip.h:EIM_CPU_RXBA]`
- `[chip.h:EIM_BUFSIZE]`
- `[chip.h:EIM_CPU_FILTER]`
- `[chip.h:EIM_CPU_DAHI]`
- `[chip.h:EIM_CPU_DALO]`
- `[chip.h:EIM_MFVHI]`
- `[chip.h:EIM_MFVLO]`
- `[chip.h:EIM_MFMHI]`
- `[c5471_ethernet.c:arm_netinitialize]`
- `[c5471_irq.c:up_irqinitialize]`
- `[c5471_irq.c:up_disable_irq]`
- `[c5471_irq.c:up_enable_irq]`
- `[c5471_irq.c:arm_ack_irq]`
- `[c5471_serial.c:arm_earlyserialinit]`
- `[c5471_serial.c:arm_serialinit]`
- `[c5471_serial.c:up_putc]`
- `[c5471_timerisr.c:up_timer_initialize]`
- `[c5471_watchdog.c:arm_wdtinit]`
- `[Kconfig:CONFIG_UART_IRDA_BAUD]`
- `[Kconfig:CONFIG_UART_IRDA_PARITY]`
- `[Kconfig:CONFIG_UART_IRDA_BITS]`
- `[Kconfig:CONFIG_UART_IRDA_2STOP]`
- `[Kconfig:CONFIG_UART_IRDA_RXBUFSIZE]`
- `[Kconfig:CONFIG_UART_IRDA_TXBUFSIZE]`
- `[Kconfig:CONFIG_UART_MODEM_BAUD]`
- `[Kconfig:CONFIG_UART_MODEM_PARITY]`

## Invariants
- `[c5471_ethernet.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[c5471_ethernet.c:#error]` Compile-time configuration constraint: Work queue support is required in this configuration (CONFIG_SCHED_WORKQUEUE)
- `[c5471_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[c5471_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[c5471_ethernet.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[c5471_ethernet.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[c5471_ethernet.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[c5471_ethernet.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[c5471_ethernet.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[c5471_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[c5471_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[c5471_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[c5471_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[c5471_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[c5471_serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[c5471_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
