# z16 (`nuttx/arch/z16`)

## Overview
Architectural grouping for `nuttx/arch/z16` (Z16 Configuration Options), coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/z16/include`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/z16/src`, coordinating 2 component subdirectories (`common`, `z16f`).

## Interface
- `[Kconfig:CONFIG_ARCH_CHIP_Z16F2810]`
- `[Kconfig:CONFIG_ARCH_CHIP_Z16F2811]`
- `[Kconfig:CONFIG_ARCH_CHIP_Z16F3211]`
- `[Kconfig:CONFIG_ARCH_CHIP_Z16F6411]`
- `[Kconfig:CONFIG_ARCH_CHIP_Z16_CUSTOM]`
- `[Kconfig:CONFIG_ARCH_CHIP_Z16F]`
- `[Kconfig:CONFIG_ARCH_CHIP]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

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
