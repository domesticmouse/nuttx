# sparc (`nuttx/arch/sparc`)

## Overview
Architectural grouping for `nuttx/arch/sparc`, coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/sparc/include`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `elf.h`, `inttypes.h`, `irq.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/sparc/src`, coordinating 5 component subdirectories (`bm3803`, `bm3823`, `common`, `s698pm`, `sparc_v8`).

## Interface
- `[Kconfig:CONFIG_ARCH_CHIP_BM3803]`
- `[Kconfig:CONFIG_ARCH_CHIP_BM3823]`
- `[Kconfig:CONFIG_ARCH_CHIP_S698PM]`
- `[Kconfig:CONFIG_ARCH_SPARC_V8]`
- `[Kconfig:CONFIG_ARCH_FAMILY]`
- `[Kconfig:CONFIG_ARCH_CHIP]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported SPARC chip
- `[bm3803-irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bm3803-serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bm3803-serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[bm3803-serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[bm3803-serial.c:#error]` Compile-time configuration constraint: I'm confused... Do we have a serial console or not?

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[bm3803.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[bm3803-irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[bm3803-irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[bm3803-irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[bm3803-serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
