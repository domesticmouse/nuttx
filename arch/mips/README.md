# mips (`nuttx/arch/mips`)

## Overview
Architectural grouping for `nuttx/arch/mips`, coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/mips/include`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `elf.h`, `inttypes.h`, `irq.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/mips/src`, coordinating 5 component subdirectories (`common`, `jz4780`, `mips32`, `pic32mx`, `pic32mz`).

## Interface
- `[Kconfig:CONFIG_ARCH_CHIP_PIC32MX]`
- `[Kconfig:CONFIG_ARCH_CHIP_PIC32MZ]`
- `[Kconfig:CONFIG_ARCH_CHIP_JZ4780]`
- `[Kconfig:CONFIG_ARCH_CHIP_MIPS_CUSTOM]`
- `[Kconfig:CONFIG_ARCH_MIPS32]`
- `[Kconfig:CONFIG_ARCH_MIPS_M4K]`
- `[Kconfig:CONFIG_ARCH_MIPS_MICROAPTIV]`
- `[Kconfig:CONFIG_ARCH_MIPS_M5150]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[mips_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mips_exit.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[mips_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[mips_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[mips_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[mips_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[syscall.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[mips_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[mips_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[mips_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[mips_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
