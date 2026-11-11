# src (`nuttx/arch/z80/src`)

## Overview
Architectural grouping for `nuttx/arch/z80/src`, coordinating 5 component subdirectories (`common`, `ez80`, `z180`, `z8`, `z80`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/z80/src/common`, providing 1 header file(s) and 12 source file(s) (including `z80_internal.h`, `z80_allocateheap.c`, `z80_createstack.c`, `z80_doirq.c`).
- `ez80`: [./ez80/README.md](./ez80/README.md) - Hardware abstraction and architecture package for `ez80` (ez80 Peripheral Support) under `nuttx/arch/z80/src/ez80`, providing 9 header file(s) and 14 source file(s) (including `chip.h`, `ez80_i2c.h`, `ez80_rtc.h`, `ez80_spi.h`).
- `z180`: [./z180/README.md](./z180/README.md) - Hardware abstraction and architecture package for `z180` (Z180 Peripheral Support; UART0 Configuration) under `nuttx/arch/z80/src/z180`, providing 7 header file(s) and 14 source file(s) (including `chip.h`, `switch.h`, `z180_config.h`, `z180_iomap.h`).
- `z8`: [./z8/README.md](./z8/README.md) - Hardware abstraction and architecture package for `z8` under `nuttx/arch/z80/src/z8`, providing 3 header file(s) and 9 source file(s) (including `chip.h`, `switch.h`, `z80_mem.h`, `z8_i2c.c`).
- `z80`: [./z80/README.md](./z80/README.md) - Hardware abstraction and architecture package for `z80` under `nuttx/arch/z80/src/z80`, providing 3 header file(s) and 7 source file(s) (including `chip.h`, `switch.h`, `z80_mem.h`, `z80_copystate.c`).

## Interface
- [./common/README.md](./common/README.md)
- [./ez80/README.md](./ez80/README.md)
- [./z180/README.md](./z180/README.md)
- [./z8/README.md](./z8/README.md)
- [./z80/README.md](./z80/README.md)

## Invariants
- `[z80_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z80_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[z80_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[chip.h:#error]` Compile-time guard: Register definitions not provided for this chip
- `[ez80_emac.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ez80_emac.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[z80_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[z80_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[z80_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[ez80_emac.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ez80_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[ez80_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
