# tricore (`nuttx/arch/tricore`)

## Overview
Architectural grouping for `nuttx/arch/tricore` (Tricore Options), coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/tricore/include`, providing 9 header file(s) and 0 source file(s) (including `arch.h`, `barriers.h`, `csfr.h`, `inttypes.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/tricore/src`, coordinating 4 component subdirectories (`common`, `illd`, `tc3xx`, `tc4xx`).

## Interface
- `[Kconfig:CONFIG_TRICORE_TOOLCHAIN_TASKING]`
- `[Kconfig:CONFIG_TRICORE_TOOLCHAIN_GNU]`
- `[Kconfig:CONFIG_ARCH_TC1V6]`
- `[Kconfig:CONFIG_ARCH_TC1V8]`
- `[Kconfig:CONFIG_ARCH_FAMILY]`
- `[Kconfig:CONFIG_ARCH_CHIP_TC3XX]`
- `[Kconfig:CONFIG_ARCH_CHIP_TC4XX]`
- `[Kconfig:CONFIG_ARCH_CHIP]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[tricore_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tricore_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tricore_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[tricore_exit.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[tricore_irq.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[tricore_mpu.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[arch.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[barriers.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[syscall.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[tricore_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[tricore_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers

## Verification
- Run: `make test`
