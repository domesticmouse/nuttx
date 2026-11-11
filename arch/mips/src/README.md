# src (`nuttx/arch/mips/src`)

## Overview
Architectural grouping for `nuttx/arch/mips/src`, coordinating 5 component subdirectories (`common`, `jz4780`, `mips32`, `pic32mx`, `pic32mz`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/mips/src/common`, providing 1 header file(s) and 15 source file(s) (including `mips_internal.h`, `mips_allocateheap.c`, `mips_createstack.c`, `mips_etherstub.c`).
- `jz4780`: [./jz4780/README.md](./jz4780/README.md) - Hardware abstraction and architecture package for `jz4780` (JZ4780 Configuration Options; JZ4780 Peripheral Support) under `nuttx/arch/mips/src/jz4780`, providing 8 header file(s) and 12 source file(s) (including `chip.h`, `jz4780_cache.h`, `jz4780_ehci.h`, `jz4780_excptmacros.h`).
- `mips32`: [./mips32/README.md](./mips32/README.md) - Hardware abstraction and architecture package for `mips32` (MIPS32 Configuration Options) under `nuttx/arch/mips/src/mips32`, providing 2 header file(s) and 11 source file(s) (including `mips32-memorymap.h`, `mips_fork.h`, `mips_copystate.c`, `mips_doirq.c`).
- `pic32mx`: [./pic32mx/README.md](./pic32mx/README.md) - Hardware abstraction and architecture package for `pic32mx` (PIC32MX Configuration Options; PIC32MX Peripheral Support) under `nuttx/arch/mips/src/pic32mx`, providing 31 header file(s) and 12 source file(s) (including `chip.h`, `excptmacros.h`, `pic32mx.h`, `pic32mx_adc.h`).
- `pic32mz`: [./pic32mz/README.md](./pic32mz/README.md) - Hardware abstraction and architecture package for `pic32mz` (PIC32MZ Configuration Options; PIC32MZ Peripheral Support) under `nuttx/arch/mips/src/pic32mz`, providing 16 header file(s) and 24 source file(s) (including `pic32mz_ba414e.h`, `pic32mz_config.h`, `pic32mz_dma.h`, `pic32mz_excptmacros.h`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./common/README.md](./common/README.md)
- [./jz4780/README.md](./jz4780/README.md)
- [./mips32/README.md](./mips32/README.md)
- [./pic32mx/README.md](./pic32mx/README.md)
- [./pic32mz/README.md](./pic32mz/README.md)

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

## Verification
- Run: `make test`
