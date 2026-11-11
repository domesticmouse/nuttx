# or1k (`nuttx/arch/or1k`)

## Overview
Architectural grouping for `nuttx/arch/or1k` (OpenRISC Options), coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/or1k/include`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/or1k/src`, coordinating 2 component subdirectories (`common`, `mor1kx`).

## Interface
- `[Kconfig:CONFIG_ARCH_CHIP_MOR1KX]`
- `[Kconfig:CONFIG_ARCH_CHIP_OR1K_CUSTOM]`
- `[Kconfig:CONFIG_ARCH_CHIP]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[arch.h:#error]` Compile-time guard: Only pages sizes of 4096 are currently supported (CONFIG_ARCH_ADDRENV)
- `[or1k_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[or1k_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[or1k_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[or1k_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[or1k_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[spr.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[or1k_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[or1k_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[or1k_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[or1k_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
