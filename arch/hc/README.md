# hc (`nuttx/arch/hc`)

## Overview
Architectural grouping for `nuttx/arch/hc`, coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/hc/include`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/hc/src`, coordinating 2 component subdirectories (`common`, `m9s12`).

## Interface
- `[Kconfig:CONFIG_ARCH_CHIP_MCS92S12NEC64]`
- `[Kconfig:CONFIG_ARCH_CHIP_HC_CUSTOM]`
- `[Kconfig:CONFIG_ARCH_HSC12]`
- `[Kconfig:CONFIG_ARCH_CHIP]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[hc_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[hc_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[hc_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[hc_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[hc_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[hc_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[hc_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[hc_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[hc_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[hc_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[hc_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)

## Verification
- Run: `make test`
