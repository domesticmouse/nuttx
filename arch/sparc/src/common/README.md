# common (`nuttx/arch/sparc/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/sparc/src/common`, providing 1 header file(s) and 15 source file(s) (including `sparc_internal.h`, `sparc_allocateheap.c`, `sparc_checkstack.c`, `sparc_createstack.c`).

## Interface
- `[sparc_internal.h:modifyreg8]`
- `[sparc_internal.h:modifyreg16]`
- `[sparc_internal.h:modifyreg32]`
- `[sparc_internal.h:sparc_copystate]`
- `[sparc_internal.h:sparc_lowputs]`
- `[sparc_internal.h:sparc_swint0]`
- `[sparc_internal.h:sparc_swint1]`
- `[sparc_internal.h:sparc_sigdeliver]`
- `[sparc_internal.h:sparc_pending_irq]`
- `[sparc_internal.h:sparc_clrpend_irq]`
- `[sparc_internal.h:sparc_dma_initialize]`
- `[sparc_internal.h:sparc_addregion]`
- `[sparc_internal.h:sparc_lowputc]`
- `[sparc_internal.h:sparc_earlyserialinit]`
- `[sparc_internal.h:sparc_serialinit]`
- `[sparc_internal.h:sparc_netinitialize]`
- `[sparc_internal.h:sparc_usbinitialize]`
- `[sparc_internal.h:sparc_usbuninitialize]`
- `[sparc_internal.h:sparc_stack_check]`
- `[sparc_internal.h:sparc_stack_color]`
- `[sparc_internal.h:sparc_color_intstack]`
- `[sparc_internal.h:USE_SERIALDRIVER]`
- `[sparc_internal.h:USE_EARLYSERIALINIT]`
- `[sparc_internal.h:CONFIG_ARCH_INTERRUPTSTACK]`
- `[sparc_internal.h:INTSTACK_SIZE]`
- `[sparc_internal.h:STACK_COLOR]`
- `[sparc_internal.h:INTSTACK_COLOR]`
- `[sparc_internal.h:HEAP_COLOR]`
- `[sparc_internal.h:getreg8]`
- `[sparc_internal.h:putreg8]`

## Invariants
- `[sparc_exit.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[sparc_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[sparc_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[sparc_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[sparc_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[sparc_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[sparc_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[sparc_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[sparc_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[sparc_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[sparc_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sparc_modifyreg32.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[sparc_modifyreg32.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[sparc_modifyreg8.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)

## Verification
- Run: `make test`
