# src (`nuttx/arch/tricore/src`)

## Overview
Architectural grouping for `nuttx/arch/tricore/src`, coordinating 4 component subdirectories (`common`, `illd`, `tc3xx`, `tc4xx`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/tricore/src/common`, providing 2 header file(s) and 32 source file(s) (including `tricore_internal.h`, `tricore_mpu.h`, `tricore_allocateheap.c`, `tricore_backtrace.c`).
- `illd`: [./illd/README.md](./illd/README.md) - Architectural grouping for `nuttx/arch/tricore/src/illd`, coordinating 2 component subdirectories (`tc3xx`, `tc4xx`).
- `tc3xx`: [./tc3xx/README.md](./tc3xx/README.md) - Hardware abstraction and architecture package for `tc3xx` (TC3XX Configuration Options; TC3XX Peripheral Support) under `nuttx/arch/tricore/src/tc3xx`, providing 1 header file(s) and 2 source file(s) (including `chip.h`, `tc3xx_serial.c`, `tc3xx_timerisr.c`).
- `tc4xx`: [./tc4xx/README.md](./tc4xx/README.md) - Hardware abstraction and architecture package for `tc4xx` (TC4XX Configuration Options; TC4XX Peripheral Support) under `nuttx/arch/tricore/src/tc4xx`, providing 1 header file(s) and 2 source file(s) (including `chip.h`, `tc4xx_serial.c`, `tc4xx_timerisr.c`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./common/README.md](./common/README.md)
- [./illd/README.md](./illd/README.md)
- [./tc3xx/README.md](./tc3xx/README.md)
- [./tc4xx/README.md](./tc4xx/README.md)

## Invariants
- `[tricore_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tricore_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tricore_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[tricore_exit.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[tricore_irq.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[tricore_mpu.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[tricore_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[tricore_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[tricore_cache.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[tricore_cache.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[tricore_cache.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[tricore_hwdebug.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
