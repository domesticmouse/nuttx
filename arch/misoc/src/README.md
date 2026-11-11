# src (`nuttx/arch/misoc/src`)

## Overview
Architectural grouping for `nuttx/arch/misoc/src`, coordinating 3 component subdirectories (`common`, `lm32`, `minerva`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/misoc/src/common`, providing 1 header file(s) and 10 source file(s) (including `misoc.h`, `misoc_flushcache.c`, `misoc_initialize.c`, `misoc_lowputs.c`).
- `lm32`: [./lm32/README.md](./lm32/README.md) - Hardware abstraction and architecture package for `lm32` under `nuttx/arch/misoc/src/lm32`, providing 3 header file(s) and 19 source file(s) (including `chip.h`, `lm32.h`, `lm32_config.h`, `lm32_allocateheap.c`).
- `minerva`: [./minerva/README.md](./minerva/README.md) - Hardware abstraction and architecture package for `minerva` under `nuttx/arch/misoc/src/minerva`, providing 3 header file(s) and 20 source file(s) (including `chip.h`, `minerva.h`, `minerva_config.h`, `minerva_allocateheap.c`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./common/README.md](./common/README.md)
- [./lm32/README.md](./lm32/README.md)
- [./minerva/README.md](./minerva/README.md)

## Invariants
- `[misoc_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[misoc_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[misoc_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[misoc_net.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[misoc_net.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[misoc_net.c:#error]` Compile-time configuration constraint: High priority work queue support is required

## Side Effects
- `[misoc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[misoc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[misoc.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[misoc_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[misoc_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[misoc_modifyreg32.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)

## Verification
- Run: `make test`
