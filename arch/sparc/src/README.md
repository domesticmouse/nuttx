# src (`nuttx/arch/sparc/src`)

## Overview
Architectural grouping for `nuttx/arch/sparc/src`, coordinating 5 component subdirectories (`bm3803`, `bm3823`, `common`, `s698pm`, `sparc_v8`).

## Subdirectories & Boundaries
- `bm3803`: [./bm3803/README.md](./bm3803/README.md) - Hardware abstraction and architecture package for `bm3803` (BM3803 Configuration Options; BM3803 Peripheral Support) under `nuttx/arch/sparc/src/bm3803`, providing 10 header file(s) and 13 source file(s) (including `bm3803-config.h`, `bm3803-memorymap.h`, `bm3803-uart.h`, `bm3803.h`).
- `bm3823`: [./bm3823/README.md](./bm3823/README.md) - Hardware abstraction and architecture package for `bm3823` (BM3823 Configuration Options; BM3823 Peripheral Support) under `nuttx/arch/sparc/src/bm3823`, providing 5 header file(s) and 5 source file(s) (including `bm3823-config.h`, `bm3823-memorymap.h`, `bm3823-uart.h`, `bm3823.h`).
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/sparc/src/common`, providing 1 header file(s) and 15 source file(s) (including `sparc_internal.h`, `sparc_allocateheap.c`, `sparc_checkstack.c`, `sparc_createstack.c`).
- `s698pm`: [./s698pm/README.md](./s698pm/README.md) - Hardware abstraction and architecture package for `s698pm` (S698PM Configuration Options; S698PM Peripheral Support) under `nuttx/arch/sparc/src/s698pm`, providing 7 header file(s) and 11 source file(s) (including `chip.h`, `s698pm-config.h`, `s698pm-memorymap.h`, `s698pm-uart.h`).
- `sparc_v8`: [./sparc_v8/README.md](./sparc_v8/README.md) - Hardware abstraction and architecture package for `sparc_v8` (SPARC Configuration Options) under `nuttx/arch/sparc/src/sparc_v8`, providing 1 header file(s) and 12 source file(s) (including `sparc_v8.h`, `sparc_v8_copystate.c`, `sparc_v8_doirq.c`, `sparc_v8_initialstate.c`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./bm3803/README.md](./bm3803/README.md)
- [./bm3823/README.md](./bm3823/README.md)
- [./common/README.md](./common/README.md)
- [./s698pm/README.md](./s698pm/README.md)
- [./sparc_v8/README.md](./sparc_v8/README.md)

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported SPARC chip
- `[bm3803-irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bm3803-serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bm3803-serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[bm3803-serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[bm3803-serial.c:#error]` Compile-time configuration constraint: I'm confused... Do we have a serial console or not?

## Side Effects
- `[bm3803.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[bm3803-irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[bm3803-irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[bm3803-irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[bm3803-serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[bm3803-serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
