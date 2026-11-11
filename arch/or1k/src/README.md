# src (`nuttx/arch/or1k/src`)

## Overview
Architectural grouping for `nuttx/arch/or1k/src`, coordinating 2 component subdirectories (`common`, `mor1kx`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/or1k/src/common`, providing 1 header file(s) and 26 source file(s) (including `or1k_internal.h`, `or1k_allocateheap.c`, `or1k_checkstack.c`, `or1k_copyfullstate.c`).
- `mor1kx`: [./mor1kx/README.md](./mor1kx/README.md) - Hardware abstraction and architecture package for `mor1kx` (OpenRISC Configuration Options; OpenRISC Options) under `nuttx/arch/or1k/src/mor1kx`, providing 1 header file(s) and 3 source file(s) (including `mor1kx_start.h`, `mor1kx_serial.c`, `mor1kx_start.c`, `or1k_irq.c`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./common/README.md](./common/README.md)
- [./mor1kx/README.md](./mor1kx/README.md)

## Invariants
- `[or1k_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[or1k_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[or1k_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[or1k_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[or1k_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[or1k_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[or1k_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[or1k_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[or1k_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[or1k_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[or1k_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[or1k_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
