# z80 (`nuttx/arch/z80/src/z80`)

## Overview
Hardware abstraction and architecture package for `z80` under `nuttx/arch/z80/src/z80`, providing 3 header file(s) and 7 source file(s) (including `chip.h`, `switch.h`, `z80_mem.h`, `z80_copystate.c`).

## Interface
- `[switch.h:z80_copystate]`
- `[switch.h:up_saveusercontext]`
- `[switch.h:z80_restoreusercontext]`
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
- `[z80_mem.h:CONFIG_STACK_END]`
- `[z80_mem.h:CONFIG_STACK_BASE]`
- `[z80_mem.h:CONFIG_HEAP1_END]`
- `[z80_mem.h:CONFIG_HEAP1_BASE]`
- `[z80_copystate.c:z80_copystate]`
- `[z80_initialstate.c:up_initial_state]`
- `[z80_io.c:outp]`
- `[z80_registerdump.c:up_dump_register]`
- `[z80_schedulesigaction.c:up_schedule_sigaction]`
- `[z80_sigdeliver.c:z80_sigdeliver]`
- `[Kconfig:CONFIG_Z80_TOOLCHAIN_SDCC]`
- `[Kconfig:CONFIG_LINKER_HOME_AREA]`
- `[Kconfig:CONFIG_LINKER_CODE_AREA]`
- `[Kconfig:CONFIG_LINKER_DATA_AREA]`
- `[Kconfig:CONFIG_LINKER_ROM_AT_0000]`
- `[Kconfig:CONFIG_ARCH_HAVEHEAD]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- `[z80_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[z80_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z80_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- None

## Verification
- Run: `make test`
