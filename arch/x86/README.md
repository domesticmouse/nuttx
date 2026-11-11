# x86 (`nuttx/arch/x86`)

## Overview
Architectural grouping for `nuttx/arch/x86` (x86 Configuration Options), coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/x86/include`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `io.h`, `irq.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/x86/src`, coordinating 3 component subdirectories (`common`, `i486`, `qemu`).

## Interface
- `[Kconfig:CONFIG_ARCH_CHIP_QEMU_I486]`
- `[Kconfig:CONFIG_ARCH_CHIP_X86_CUSTOM]`
- `[Kconfig:CONFIG_ARCH_I486]`
- `[Kconfig:CONFIG_ARCH_CHIP]`
- `[Kconfig:CONFIG_ARCH_X86_HAVE_32BIT]`
- `[Kconfig:CONFIG_ARCH_X86_M32]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

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
