# common (`nuttx/arch/mips/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/mips/src/common`, providing 1 header file(s) and 15 source file(s) (including `mips_internal.h`, `mips_allocateheap.c`, `mips_createstack.c`, `mips_etherstub.c`).

## Interface
- `[mips_internal.h:modifyreg8]`
- `[mips_internal.h:modifyreg16]`
- `[mips_internal.h:modifyreg32]`
- `[mips_internal.h:mips_copystate]`
- `[mips_internal.h:mips_lowputs]`
- `[mips_internal.h:mips_doirq]`
- `[mips_internal.h:mips_swint0]`
- `[mips_internal.h:mips_sigdeliver]`
- `[mips_internal.h:mips_pending_irq]`
- `[mips_internal.h:mips_clrpend_irq]`
- `[mips_internal.h:mips_clrpend_sw0]`
- `[mips_internal.h:mips_dma_initialize]`
- `[mips_internal.h:mips_addregion]`
- `[mips_internal.h:mips_lowputc]`
- `[mips_internal.h:mips_earlyserialinit]`
- `[mips_internal.h:mips_serialinit]`
- `[mips_internal.h:mips_netinitialize]`
- `[mips_internal.h:mips_usbinitialize]`
- `[mips_internal.h:mips_usbuninitialize]`
- `[mips_internal.h:USE_SERIALDRIVER]`
- `[mips_internal.h:USE_EARLYSERIALINIT]`
- `[mips_internal.h:CONFIG_ARCH_INTERRUPTSTACK]`
- `[mips_internal.h:getreg8]`
- `[mips_internal.h:putreg8]`
- `[mips_internal.h:getreg16]`
- `[mips_internal.h:putreg16]`
- `[mips_internal.h:getreg32]`
- `[mips_internal.h:putreg32]`
- `[mips_internal.h:mips_savestate]`
- `[mips_internal.h:mips_restorestate]`

## Invariants
- `[mips_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mips_exit.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[mips_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[mips_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[mips_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[mips_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[mips_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[mips_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[mips_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[mips_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[mips_idle.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[mips_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[mips_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[mips_modifyreg32.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[mips_modifyreg32.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[mips_modifyreg8.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)

## Verification
- Run: `make test`
