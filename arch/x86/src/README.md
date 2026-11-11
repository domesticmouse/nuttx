# src (`nuttx/arch/x86/src`)

## Overview
Architectural grouping for `nuttx/arch/x86/src`, coordinating 3 component subdirectories (`common`, `i486`, `qemu`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` (Common Configuration Options) under `nuttx/arch/x86/src/common`, providing 2 header file(s) and 13 source file(s) (including `x86_fork.h`, `x86_internal.h`, `x86_allocateheap.c`, `x86_copystate.c`).
- `i486`: [./i486/README.md](./i486/README.md) - Hardware abstraction and architecture package for `i486` (i486 Configuration Options) under `nuttx/arch/x86/src/i486`, providing 0 header file(s) and 10 source file(s) (including `i486_createstack.c`, `i486_initialstate.c`, `i486_irq.c`, `i486_regdump.c`).
- `qemu`: [./qemu/README.md](./qemu/README.md) - Hardware abstraction and architecture package for `qemu` (QEMU Configuration Options) under `nuttx/arch/x86/src/qemu`, providing 5 header file(s) and 8 source file(s) (including `chip.h`, `qemu.h`, `qemu_keypad.h`, `qemu_memorymap.h`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./common/README.md](./common/README.md)
- [./i486/README.md](./i486/README.md)
- [./qemu/README.md](./qemu/README.md)

## Invariants
- `[x86_fork.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_fork.c:#error]` Compile-time configuration constraint: x86 relocates the vfork() child stack; borrowing is not supported
- `[x86_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[x86_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[x86_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[i486_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[x86_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[x86_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[x86_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[x86_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[x86_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[x86_modifyreg32.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)

## Verification
- Run: `make test`
