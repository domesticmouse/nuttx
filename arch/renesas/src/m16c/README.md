# m16c (`nuttx/arch/renesas/src/m16c`)

## Overview
Hardware abstraction and architecture package for `m16c` under `nuttx/arch/renesas/src/m16c`, providing 3 header file(s) and 9 source file(s) (including `chip.h`, `m16c_timer.h`, `m16c_uart.h`, `m16c_copystate.c`).

## Interface
- `[chip.h:M16C_FLG_C]`
- `[chip.h:M16C_FLG_D]`
- `[chip.h:M16C_FLG_Z]`
- `[chip.h:M16C_FLG_S]`
- `[chip.h:M16C_FLG_B]`
- `[chip.h:M16C_FLG_O]`
- `[chip.h:M16C_FLG_I]`
- `[chip.h:M16C_FLG_U]`
- `[chip.h:M16C_FLG_IPLMASK]`
- `[chip.h:M16C_SFR_BASE]`
- `[chip.h:M16C_IRAM_BASE]`
- `[chip.h:M16C_IRAM_END]`
- `[m16c_timer.h:M16C_TA0IC]`
- `[m16c_timer.h:M16C_TA1IC]`
- `[m16c_timer.h:M16C_TA2IC]`
- `[m16c_timer.h:M16C_TA3IC]`
- `[m16c_timer.h:M16C_TA4IC]`
- `[m16c_timer.h:TABSR_TA0S]`
- `[m16c_timer.h:TABSR_TA1S]`
- `[m16c_timer.h:TABSR_TA2S]`
- `[m16c_timer.h:TABSR_TA3S]`
- `[m16c_timer.h:TABSR_TA4S]`
- `[m16c_timer.h:TABSR_TB0S]`
- `[m16c_timer.h:TABSR_TB1S]`
- `[m16c_uart.h:M16C_UART0_BASE]`
- `[m16c_uart.h:M16C_UART1_BASE]`
- `[m16c_uart.h:M16C_UART2_BASE]`
- `[m16c_uart.h:M16C_UART_MR]`
- `[m16c_uart.h:M16C_UART_BRG]`
- `[m16c_uart.h:M16C_UART_TB]`

## Invariants
- `[m16c_lowputc.c:#error]` Compile-time configuration constraint: A serial console selected, but corresponding UART not enabled
- `[m16c_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[m16c_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[m16c_serial.c:#error]` Compile-time configuration constraint: Serial driver selected, but No UARTs is enabled
- `[m16c_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[m16c_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[m16c_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[m16c_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[m16c_lowputc.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[m16c_lowputc.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[m16c_serial.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[m16c_serial.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[m16c_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[m16c_timerisr.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[m16c_timerisr.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[m16c_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[m16c_timerisr.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
