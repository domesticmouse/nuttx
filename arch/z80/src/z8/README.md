# z8 (`nuttx/arch/z80/src/z8`)

## Overview
Hardware abstraction and architecture package for `z8` under `nuttx/arch/z80/src/z8`, providing 3 header file(s) and 9 source file(s) (including `chip.h`, `switch.h`, `z80_mem.h`, `z8_i2c.c`).

## Interface
- `[chip.h:_HX]`
- `[chip.h:Z8_TIMERCTL_TEN]`
- `[chip.h:Z8_TIMERCTL_TPOL]`
- `[chip.h:Z8_TIMERCTL_DIV1]`
- `[chip.h:Z8_TIMERCTL_DIV2]`
- `[chip.h:Z8_TIMERCTL_DIV4]`
- `[chip.h:Z8_TIMERCTL_DIV8]`
- `[chip.h:Z8_TIMERCTL_DIV16]`
- `[chip.h:Z8_TIMERCTL_DIV32]`
- `[chip.h:Z8_TIMERCTL_DIV64]`
- `[chip.h:Z8_TIMERCTL_DIV128]`
- `[switch.h:up_ack_irq]`
- `[switch.h:up_saveusercontext]`
- `[switch.h:z8_saveirqcontext]`
- `[switch.h:z8_restorecontext]`
- `[switch.h:z8_sigsetup]`
- `[switch.h:z8_irqstate_s]`
- `[switch.h:Z8_IRQSTATE_NONE]`
- `[switch.h:Z8_IRQSTATE_ENTRY]`
- `[switch.h:Z8_IRQSTATE_SAVED]`
- `[switch.h:Z8_IRQSAVE_RPFLAGS]`
- `[switch.h:Z8_IRQSAVE_PC]`
- `[switch.h:Z8_IRQSAVE_REGS]`
- `[switch.h:Z8_IRQSAVE_RP_OFFS]`
- `[switch.h:Z8_IRQSAVE_FLAGS_OFFS]`
- `[switch.h:Z8_IRQSAVE_PCH_OFFS]`
- `[switch.h:Z8_IRQSAVE_PCL_OFFS]`
- `[switch.h:Z8_IRQSAVE_SIZE]`
- `[switch.h:INIT_IRQCONTEXT]`
- `[z80_mem.h:CONFIG_HEAP1_BASE]`

## Invariants
- `[z8_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z8_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[z8_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z8_serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[z8_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z8_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[z8_irq.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[z8_irq.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[z8_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[z8_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[z8_serial.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[z8_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[z8_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[z8_serial.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[z8_timerisr.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[z8_timerisr.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[z8_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[z8_timerisr.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
