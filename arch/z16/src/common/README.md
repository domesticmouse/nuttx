# common (`nuttx/arch/z16/src/common`)

## Overview
Hardware abstraction and architecture package for `common` (Common Configuration Options) under `nuttx/arch/z16/src/common`, providing 1 header file(s) and 16 source file(s) (including `z16_internal.h`, `z16_allocateheap.c`, `z16_copystate.c`, `z16_createstack.c`).

## Interface
- `[z16_internal.h:z16_copystate]`
- `[z16_internal.h:z16_doirq]`
- `[z16_internal.h:z16_restoreusercontext]`
- `[z16_internal.h:z16_sigdeliver]`
- `[z16_internal.h:z16_lowputc]`
- `[z16_internal.h:z16_addregion]`
- `[z16_internal.h:z16_serialinit]`
- `[z16_internal.h:z16_earlyserialinit]`
- `[z16_internal.h:z16_ack_irq]`
- `[z16_internal.h:z16_netinitialize]`
- `[z16_internal.h:USE_LOWUARTINIT]`
- `[z16_internal.h:USE_SERIALDRIVER]`
- `[z16_internal.h:USE_EARLYSERIALINIT]`
- `[z16_internal.h:IN_INTERRUPT]`
- `[z16_internal.h:SAVE_IRQCONTEXT]`
- `[z16_internal.h:SET_IRQCONTEXT]`
- `[z16_internal.h:SAVE_USERCONTEXT]`
- `[z16_internal.h:RESTORE_USERCONTEXT]`
- `[z16_internal.h:SIGNAL_RETURN]`
- `[z16_internal.h:getreg8]`
- `[z16_internal.h:putreg8]`
- `[z16_allocateheap.c:up_allocate_heap]`
- `[z16_allocateheap.c:z16_addregion]`
- `[z16_copystate.c:z16_copystate]`
- `[z16_createstack.c:up_create_stack]`
- `[z16_doirq.c:z16_doirq]`
- `[z16_exit.c:up_exit]`
- `[z16_idle.c:up_idle]`
- `[z16_initialize.c:up_initialize]`
- `[z16_initialstate.c:up_initial_state]`

## Invariants
- `[z16_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z16_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[z16_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z16_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[z16_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[z16_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[z16_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[z16_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
