# common (`nuttx/arch/x86/src/common`)

## Overview
Hardware abstraction and architecture package for `common` (Common Configuration Options) under `nuttx/arch/x86/src/common`, providing 2 header file(s) and 13 source file(s) (including `x86_fork.h`, `x86_internal.h`, `x86_allocateheap.c`, `x86_copystate.c`).

## Interface
- `[x86_fork.h:x86_fork]`
- `[x86_fork.h:fork_s]`
- `[x86_fork.h:FORK_SIZEOF]`
- `[x86_internal.h:modifyreg8]`
- `[x86_internal.h:modifyreg16]`
- `[x86_internal.h:modifyreg32]`
- `[x86_internal.h:x86_boardinitialize]`
- `[x86_internal.h:x86_copystate]`
- `[x86_internal.h:x86_savestate]`
- `[x86_internal.h:x86_decodeirq]`
- `[x86_internal.h:x86_dma_initialize]`
- `[x86_internal.h:x86_switchcontext]`
- `[x86_internal.h:x86_sigdeliver]`
- `[x86_internal.h:x86_lowputc]`
- `[x86_internal.h:x86_lowputs]`
- `[x86_internal.h:x86_syscall]`
- `[x86_internal.h:x86_addregion]`
- `[x86_internal.h:x86_earlyserialinit]`
- `[x86_internal.h:x86_serialinit]`
- `[x86_internal.h:x86_netinitialize]`
- `[x86_internal.h:x86_usbinitialize]`
- `[x86_internal.h:x86_usbuninitialize]`
- `[x86_internal.h:USE_SERIALDRIVER]`
- `[x86_internal.h:USE_EARLYSERIALINIT]`
- `[x86_internal.h:CONFIG_ARCH_INTERRUPTSTACK]`
- `[x86_internal.h:getreg8]`
- `[x86_internal.h:putreg8]`
- `[x86_internal.h:getreg16]`
- `[x86_internal.h:putreg16]`
- `[x86_internal.h:getreg32]`

## Invariants
- `[x86_fork.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_fork.c:#error]` Compile-time configuration constraint: x86 relocates the vfork() child stack; borrowing is not supported
- `[x86_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[x86_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[x86_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[x86_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[x86_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[x86_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[x86_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[x86_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[x86_modifyreg32.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[x86_modifyreg32.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[x86_modifyreg8.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)

## Verification
- Run: `make test`
