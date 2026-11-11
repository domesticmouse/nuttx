# common (`nuttx/arch/or1k/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/or1k/src/common`, providing 1 header file(s) and 26 source file(s) (including `or1k_internal.h`, `or1k_allocateheap.c`, `or1k_checkstack.c`, `or1k_copyfullstate.c`).

## Interface
- `[or1k_internal.h:modifyreg8]`
- `[or1k_internal.h:modifyreg16]`
- `[or1k_internal.h:modifyreg32]`
- `[or1k_internal.h:or1k_boot]`
- `[or1k_internal.h:or1k_print_cpuinfo]`
- `[or1k_internal.h:or1k_copyfullstate]`
- `[or1k_internal.h:or1k_decodeirq]`
- `[or1k_internal.h:or1k_switchcontext]`
- `[or1k_internal.h:or1k_sigdeliver]`
- `[or1k_internal.h:or1k_pminitialize]`
- `[or1k_internal.h:or1k_ack_irq]`
- `[or1k_internal.h:or1k_doirq]`
- `[or1k_internal.h:or1k_hardfault]`
- `[or1k_internal.h:or1k_memfault]`
- `[or1k_internal.h:or1k_syscall]`
- `[or1k_internal.h:or1k_lowputc]`
- `[or1k_internal.h:or1k_lowputs]`
- `[or1k_internal.h:or1k_serialinit]`
- `[or1k_internal.h:or1k_earlyserialinit]`
- `[or1k_internal.h:or1k_dma_initialize]`
- `[or1k_internal.h:or1k_l2ccinitialize]`
- `[or1k_internal.h:or1k_addregion]`
- `[or1k_internal.h:or1k_etinitialize]`
- `[or1k_internal.h:or1k_usbinitialize]`
- `[or1k_internal.h:or1k_usbuninitialize]`
- `[or1k_internal.h:or1k_stack_check]`
- `[or1k_internal.h:or1k_stack_color]`
- `[or1k_internal.h:or1k_color_intstack]`
- `[or1k_internal.h:USE_SERIALDRIVER]`
- `[or1k_internal.h:USE_EARLYSERIALINIT]`

## Invariants
- `[or1k_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[or1k_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[or1k_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[or1k_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[or1k_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[or1k_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[or1k_pthread_start.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[or1k_task_start.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[or1k_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[or1k_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[or1k_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[or1k_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[or1k_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[or1k_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[or1k_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[or1k_modifyreg32.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[or1k_modifyreg32.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[or1k_modifyreg8.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[or1k_timer.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[or1k_timer.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
