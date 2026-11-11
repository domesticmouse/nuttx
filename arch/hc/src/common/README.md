# common (`nuttx/arch/hc/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/hc/src/common`, providing 1 header file(s) and 16 source file(s) (including `hc_internal.h`, `hc_allocateheap.c`, `hc_copystate.c`, `hc_createstack.c`).

## Interface
- `[hc_internal.h:modifyreg8]`
- `[hc_internal.h:modifyreg16]`
- `[hc_internal.h:modifyreg32]`
- `[hc_internal.h:hc_copystate]`
- `[hc_internal.h:hc_decodeirq]`
- `[hc_internal.h:hc_switchcontext]`
- `[hc_internal.h:hc_doirq]`
- `[hc_internal.h:hc_sigdeliver]`
- `[hc_internal.h:hc_earlyserialinit]`
- `[hc_internal.h:hc_serialinit]`
- `[hc_internal.h:hc_lowputc]`
- `[hc_internal.h:hc_lowputs]`
- `[hc_internal.h:hc_addregion]`
- `[hc_internal.h:hc_dma_initialize]`
- `[hc_internal.h:hc_netinitialize]`
- `[hc_internal.h:hc_usbinitialize]`
- `[hc_internal.h:hc_usbuninitialize]`
- `[hc_internal.h:USE_SERIALDRIVER]`
- `[hc_internal.h:USE_EARLYSERIALINIT]`
- `[hc_internal.h:CONFIG_ARCH_INTERRUPTSTACK]`
- `[hc_internal.h:getreg8]`
- `[hc_internal.h:putreg8]`
- `[hc_internal.h:getreg16]`
- `[hc_internal.h:putreg16]`
- `[hc_internal.h:getreg32]`
- `[hc_internal.h:putreg32]`
- `[hc_internal.h:hc_savestate]`
- `[hc_internal.h:hc_restorestate]`
- `[hc_allocateheap.c:up_allocate_heap]`
- `[hc_copystate.c:hc_copystate]`

## Invariants
- `[hc_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[hc_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[hc_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[hc_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[hc_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[hc_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[hc_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[hc_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[hc_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[hc_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[hc_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[hc_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[hc_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[hc_modifyreg32.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[hc_modifyreg32.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[hc_modifyreg8.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)

## Verification
- Run: `make test`
