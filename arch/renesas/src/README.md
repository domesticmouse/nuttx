# src (`nuttx/arch/renesas/src`)

## Overview
Architectural grouping for `nuttx/arch/renesas/src`, coordinating 4 component subdirectories (`common`, `m16c`, `rx65n`, `sh1`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/renesas/src/common`, providing 1 header file(s) and 13 source file(s) (including `renesas_internal.h`, `renesas_allocateheap.c`, `renesas_createstack.c`, `renesas_doirq.c`).
- `m16c`: [./m16c/README.md](./m16c/README.md) - Hardware abstraction and architecture package for `m16c` under `nuttx/arch/renesas/src/m16c`, providing 3 header file(s) and 9 source file(s) (including `chip.h`, `m16c_timer.h`, `m16c_uart.h`, `m16c_copystate.c`).
- `rx65n`: [./rx65n/README.md](./rx65n/README.md) - Hardware abstraction and architecture package for `rx65n` (RX65N Configuration Options; RX65N Peripheral Selections) under `nuttx/arch/renesas/src/rx65n`, providing 18 header file(s) and 26 source file(s) (including `chip.h`, `rx65n_cgc.h`, `rx65n_cmt.h`, `rx65n_cmtw.h`).
- `sh1`: [./sh1/README.md](./sh1/README.md) - Hardware abstraction and architecture package for `sh1` (SH-1 Configuration Options; SH-1 Peripheral Selections) under `nuttx/arch/renesas/src/sh1`, providing 2 header file(s) and 9 source file(s) (including `chip.h`, `sh1_703x.h`, `sh1_copystate.c`, `sh1_initialstate.c`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./common/README.md](./common/README.md)
- [./m16c/README.md](./m16c/README.md)
- [./rx65n/README.md](./rx65n/README.md)
- [./sh1/README.md](./sh1/README.md)

## Invariants
- `[renesas_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[renesas_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[renesas_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[renesas_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[m16c_lowputc.c:#error]` Compile-time configuration constraint: A serial console selected, but corresponding UART not enabled
- `[m16c_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[renesas_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[renesas_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[renesas_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[m16c_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[m16c_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[m16c_lowputc.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)

## Verification
- Run: `make test`
