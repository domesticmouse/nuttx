# src (`nuttx/arch/hc/src`)

## Overview
Architectural grouping for `nuttx/arch/hc/src`, coordinating 2 component subdirectories (`common`, `m9s12`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/hc/src/common`, providing 1 header file(s) and 16 source file(s) (including `hc_internal.h`, `hc_allocateheap.c`, `hc_copystate.c`, `hc_createstack.c`).
- `m9s12`: [./m9s12/README.md](./m9s12/README.md) - Hardware abstraction and architecture package for `m9s12` (M9S12 Configuration Options; M9S12 Peripheral Selection) under `nuttx/arch/hc/src/m9s12`, providing 16 header file(s) and 9 source file(s) (including `chip.h`, `m9s12.h`, `m9s12_atd.h`, `m9s12_crg.h`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./common/README.md](./common/README.md)
- [./m9s12/README.md](./m9s12/README.md)

## Invariants
- `[hc_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[hc_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[hc_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[hc_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[hc_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[hc_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[hc_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[hc_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[hc_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[hc_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[hc_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[hc_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
