# z16f (`nuttx/arch/z16/src/z16f`)

## Overview
Hardware abstraction and architecture package for `z16f` (Z16F Configuration Options; Z16F Peripheral Selection) under `nuttx/arch/z16/src/z16f`, providing 1 header file(s) and 6 source file(s) (including `chip.h`, `z16f_clkinit.c`, `z16f_espi.c`, `z16f_irq.c`).

## Interface
- `[chip.h:z16f_board_initialize]`
- `[chip.h:z16f_lowuartinit]`
- `[chip.h:z16f_sysexec]`
- `[chip.h:z16f_reset]`
- `[chip.h:z16_spibus_initialize]`
- `[chip.h:z16f_espi_select]`
- `[chip.h:z16f_espi_status]`
- `[chip.h:z16f_espi_cmddata]`
- `[chip.h:_HX32]`
- `[chip.h:_HX8]`
- `[chip.h:Z16F_INVMEM_SIZE]`
- `[chip.h:Z16F_IRAM_SIZE]`
- `[chip.h:Z16F_HAVE_EXTMEM]`
- `[chip.h:Z16F_HAVE_GPIO_PORTJ]`
- `[chip.h:Z16F_HAVE_GPIO_PORTK]`
- `[z16f_clkinit.c:z16f_clkinit]`
- `[z16f_espi.c:z16_spibus_initialize]`
- `[z16f_irq.c:up_irqinitialize]`
- `[z16f_irq.c:up_disable_irq]`
- `[z16f_irq.c:up_enable_irq]`
- `[z16f_irq.c:z16_ack_irq]`
- `[z16f_irq.c:up_prioritize_irq]`
- `[z16f_serial.c:z16_earlyserialinit]`
- `[z16f_serial.c:z16_serialinit]`
- `[z16f_serial.c:up_putc]`
- `[z16f_sysexec.c:z16f_sysexec]`
- `[z16f_timerisr.c:up_timer_initialize]`
- `[Kconfig:CONFIG_Z16F_ESPI]`
- `[Kconfig:CONFIG_Z16F_UART0]`
- `[Kconfig:CONFIG_Z16F_UART1]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Z16F chip variant not specified
- `[z16f_espi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z16f_espi.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[z16f_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z16f_serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[z16f_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[z16f_clkinit.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[z16f_espi.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[z16f_espi.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[z16f_irq.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[z16f_irq.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[z16f_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[z16f_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[z16f_serial.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[z16f_serial.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[z16f_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[z16f_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[z16f_serial.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
