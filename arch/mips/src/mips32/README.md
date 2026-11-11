# mips32 (`nuttx/arch/mips/src/mips32`)

## Overview
Hardware abstraction and architecture package for `mips32` (MIPS32 Configuration Options) under `nuttx/arch/mips/src/mips32`, providing 2 header file(s) and 11 source file(s) (including `mips32-memorymap.h`, `mips_fork.h`, `mips_copystate.c`, `mips_doirq.c`).

## Interface
- `[mips32-memorymap.h:USEG_BASE]`
- `[mips32-memorymap.h:USEG_SIZE]`
- `[mips32-memorymap.h:KSEG0_BASE]`
- `[mips32-memorymap.h:KSEG0_SIZE]`
- `[mips32-memorymap.h:KSEG1_BASE]`
- `[mips32-memorymap.h:KSEG1_SIZE]`
- `[mips32-memorymap.h:KSEG2_BASE]`
- `[mips32-memorymap.h:KSEG2_SIZE]`
- `[mips32-memorymap.h:KSEG3_BASE]`
- `[mips32-memorymap.h:KSEG3_SIZE]`
- `[mips32-memorymap.h:DSEG_BASE]`
- `[mips32-memorymap.h:DSEG_SIZE]`
- `[mips_fork.h:fork_s]`
- `[mips_fork.h:FORK_S0_OFFSET]`
- `[mips_fork.h:FORK_S1_OFFSET]`
- `[mips_fork.h:FORK_S2_OFFSET]`
- `[mips_fork.h:FORK_S3_OFFSET]`
- `[mips_fork.h:FORK_S4_OFFSET]`
- `[mips_fork.h:FORK_S5_OFFSET]`
- `[mips_fork.h:FORK_S6_OFFSET]`
- `[mips_fork.h:FORK_S7_OFFSET]`
- `[mips_fork.h:FORK_FP_OFFSET]`
- `[mips_fork.h:FORK_S8_OFFSET]`
- `[mips_fork.h:FORK_SP_OFFSET]`
- `[mips_fork.h:FORK_RA_OFFSET]`
- `[mips_copystate.c:mips_copystate]`
- `[mips_doirq.c:mips_doirq]`
- `[mips_fork.c:mips_fork]`
- `[mips_initialstate.c:up_initial_state]`
- `[mips_irq.c:up_irq_save]`

## Invariants
- `[mips_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mips_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[mips_fork.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mips_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[mips_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mips_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[mips_swint0.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mips_swint0.c:#error]` Compile-time configuration constraint: Missing logic

## Side Effects
- `[mips_doirq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[mips_doirq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[mips_swint0.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
