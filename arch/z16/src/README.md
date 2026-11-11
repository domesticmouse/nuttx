# src (`nuttx/arch/z16/src`)

## Overview
Architectural grouping for `nuttx/arch/z16/src`, coordinating 2 component subdirectories (`common`, `z16f`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` (Common Configuration Options) under `nuttx/arch/z16/src/common`, providing 1 header file(s) and 16 source file(s) (including `z16_internal.h`, `z16_allocateheap.c`, `z16_copystate.c`, `z16_createstack.c`).
- `z16f`: [./z16f/README.md](./z16f/README.md) - Hardware abstraction and architecture package for `z16f` (Z16F Configuration Options; Z16F Peripheral Selection) under `nuttx/arch/z16/src/z16f`, providing 1 header file(s) and 6 source file(s) (including `chip.h`, `z16f_clkinit.c`, `z16f_espi.c`, `z16f_irq.c`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./common/README.md](./common/README.md)
- [./z16f/README.md](./z16f/README.md)

## Invariants
- `[z16_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z16_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[z16_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z16_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[z16_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[chip.h:#error]` Compile-time guard: Z16F chip variant not specified

## Side Effects
- `[z16_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[z16_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[z16_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[z16f_clkinit.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[z16f_espi.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[z16f_espi.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)

## Verification
- Run: `make test`
