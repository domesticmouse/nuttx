# z180 (`nuttx/arch/z80/src/z180`)

## Overview
Hardware abstraction and architecture package for `z180` (Z180 Peripheral Support; UART0 Configuration) under `nuttx/arch/z80/src/z180`, providing 7 header file(s) and 14 source file(s) (including `chip.h`, `switch.h`, `z180_config.h`, `z180_iomap.h`).

## Interface
- `[switch.h:z180_copystate]`
- `[switch.h:up_saveusercontext]`
- `[switch.h:z180_restoreusercontext]`
- `[switch.h:z180_sigsetup]`
- `[switch.h:INIT_IRQCONTEXT]`
- `[switch.h:IN_INTERRUPT]`
- `[switch.h:DECL_SAVESTATE]`
- `[switch.h:IRQ_ENTER]`
- `[switch.h:IRQ_LEAVE]`
- `[switch.h:IRQ_STATE]`
- `[switch.h:SAVE_IRQCONTEXT]`
- `[switch.h:SET_IRQCONTEXT]`
- `[switch.h:SAVE_USERCONTEXT]`
- `[switch.h:RESTORE_USERCONTEXT]`
- `[z180_config.h:HAVE_UART]`
- `[z180_config.h:HAVE_SERIAL]`
- `[z180_config.h:HAVE_SCC]`
- `[z180_config.h:HAVE_UART_CONSOLE]`
- `[z180_config.h:HAVE_SERIAL_CONSOLE]`
- `[z180_config.h:HAVE_SCC_CONSOLE]`
- `[z180_iomap.h:SFR_OFFSET]`
- `[z180_iomap.h:Z180_ASCI0_CNTLA]`
- `[z180_iomap.h:Z180_ASCI1_CNTLA]`
- `[z180_iomap.h:Z180_ASCI0_CNTLB]`
- `[z180_iomap.h:Z180_ASCI1_CNTLB]`
- `[z180_iomap.h:Z180_ASCI0_STAT]`
- `[z180_iomap.h:Z180_ASCI1_STAT]`
- `[z180_iomap.h:Z180_ASCI0_TDR]`
- `[z180_iomap.h:Z180_ASCI1_TDR]`
- `[z180_iomap.h:Z180_ASCI0_RDR]`

## Invariants
- `[z180_mmu.h:#error]` Compile-time guard: CONFIG_Z180_BANKAREA_VIRTBASE > CONFIG_Z180_COMMON1AREA_VIRTBASE
- `[z180_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[z180_mmu.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z180_mmu.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[z180_modifiyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[z180_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z180_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[z180_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[z180_timerisr.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
