# common (`nuttx/arch/z80/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/z80/src/common`, providing 1 header file(s) and 12 source file(s) (including `z80_internal.h`, `z80_allocateheap.c`, `z80_createstack.c`, `z80_doirq.c`).

## Interface
- `[z80_internal.h:z80_doirq]`
- `[z80_internal.h:z80_sigdeliver]`
- `[z80_internal.h:z80_mmu_initialize]`
- `[z80_internal.h:z80_serial_initialize]`
- `[z80_internal.h:z80_timerhook]`
- `[z80_internal.h:z80_netinitialize]`
- `[z80_internal.h:z80_netuninitialize]`
- `[z80_internal.h:z80_multicastfilter]`
- `[z80_internal.h:USE_SERIALDRIVER]`
- `[z80_internal.h:getreg8]`
- `[z80_internal.h:putreg8]`
- `[z80_internal.h:getreg16]`
- `[z80_internal.h:putreg16]`
- `[z80_internal.h:getreg32]`
- `[z80_internal.h:putreg32]`
- `[z80_allocateheap.c:up_allocate_heap]`
- `[z80_allocateheap.c:z80_addregion]`
- `[z80_createstack.c:up_create_stack]`
- `[z80_doirq.c:z80_doirq]`
- `[z80_exit.c:up_exit]`
- `[z80_idle.c:up_idle]`
- `[z80_initialize.c:up_initialize]`
- `[z80_interruptcontext.c:up_interrupt_context]`
- `[z80_nputs.c:up_nputs]`
- `[z80_releasestack.c:up_release_stack]`
- `[z80_stackframe.c:up_stack_frame]`
- `[z80_switchcontext.c:up_switch_context]`
- `[z80_usestack.c:up_use_stack]`

## Invariants
- `[z80_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z80_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[z80_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[z80_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[z80_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[z80_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
