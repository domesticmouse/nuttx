# sh1 (`nuttx/arch/renesas/src/sh1`)

## Overview
Hardware abstraction and architecture package for `sh1` (SH-1 Configuration Options; SH-1 Peripheral Selections) under `nuttx/arch/renesas/src/sh1`, providing 2 header file(s) and 9 source file(s) (including `chip.h`, `sh1_703x.h`, `sh1_copystate.c`, `sh1_initialstate.c`).

## Interface
- `[sh1_703x.h:SH1_SCI0_BASE]`
- `[sh1_703x.h:SH1_SCI1_BASE]`
- `[sh1_703x.h:SH1_SCI_SMR_OFFSET]`
- `[sh1_703x.h:SH1_SCI_BRR_OFFSET]`
- `[sh1_703x.h:SH1_SCI_SCR_OFFSET]`
- `[sh1_703x.h:SH1_SCI_TDR_OFFSET]`
- `[sh1_703x.h:SH1_SCI_SSR_OFFSET]`
- `[sh1_703x.h:SH1_SCI_RDR_OFFSET]`
- `[sh1_703x.h:SH1_SCI0_SMR]`
- `[sh1_703x.h:SH1_SCI0_BRR]`
- `[sh1_703x.h:SH1_SCI0_SCR]`
- `[sh1_703x.h:SH1_SCI0_TDR]`
- `[sh1_copystate.c:renesas_copystate]`
- `[sh1_initialstate.c:up_initial_state]`
- `[sh1_irq.c:up_irqinitialize]`
- `[sh1_irq.c:up_prioritize_irq]`
- `[sh1_lowputc.c:renesas_lowputc]`
- `[sh1_lowputc.c:up_lowsetup]`
- `[sh1_registerdump.c:up_dump_register]`
- `[sh1_schedulesigaction.c:up_schedule_sigaction]`
- `[sh1_serial.c:renesas_earlyconsoleinit]`
- `[sh1_serial.c:renesas_consoleinit]`
- `[sh1_serial.c:up_putc]`
- `[sh1_sigdeliver.c:renesas_sigdeliver]`
- `[sh1_timerisr.c:up_timer_initialize]`
- `[Kconfig:CONFIG_SH1_DMAC0]`
- `[Kconfig:CONFIG_SH1_DMAC1]`
- `[Kconfig:CONFIG_SH1_DMAC2]`
- `[Kconfig:CONFIG_SH1_DMAC3]`
- `[Kconfig:CONFIG_SH1_ITU1]`

## Invariants
- `[sh1_initialstate.c:#error]` Compile-time configuration constraint: Missing logic for the CONFIG_BUILD_KERNEL build
- `[sh1_lowputc.c:#error]` Compile-time configuration constraint: Serial console selected, but corresponding SCI not enabled
- `[sh1_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sh1_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sh1_serial.c:#error]` Compile-time configuration constraint: Serial driver selected, but SCIs not enabled
- `[sh1_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sh1_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[sh1_timerisr.c:#error]` Compile-time configuration constraint: No divider is available for this system clock

## Side Effects
- `[sh1_initialstate.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[sh1_irq.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[sh1_lowputc.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[sh1_serial.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[sh1_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[sh1_timerisr.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[sh1_timerisr.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[sh1_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[sh1_timerisr.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
