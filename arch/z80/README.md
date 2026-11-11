# z80 (`nuttx/arch/z80`)

## Overview
Architectural grouping for `nuttx/arch/z80`, coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/z80/include`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `io.h`, `irq.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/z80/src`, coordinating 5 component subdirectories (`common`, `ez80`, `z180`, `z8`, `z80`).

## Interface
- `[Kconfig:CONFIG_ARCH_CHIP_Z80]`
- `[Kconfig:CONFIG_ARCH_CHIP_Z180]`
- `[Kconfig:CONFIG_ARCH_CHIP_EZ80]`
- `[Kconfig:CONFIG_ARCH_CHIP_Z8]`
- `[Kconfig:CONFIG_ARCH_CHIP_Z80_CUSTOM]`
- `[Kconfig:CONFIG_ARCH_CHIP]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[z80_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[z80_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[z80_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[chip.h:#error]` Compile-time guard: Register definitions not provided for this chip
- `[ez80_emac.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ez80_emac.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[z80_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[z80_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[z80_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[ez80_emac.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ez80_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
