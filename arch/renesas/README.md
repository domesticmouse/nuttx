# renesas (`nuttx/arch/renesas`)

## Overview
Architectural grouping for `nuttx/arch/renesas`, coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/renesas/include`, providing 9 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/renesas/src`, coordinating 4 component subdirectories (`common`, `m16c`, `rx65n`, `sh1`).

## Interface
- `[Kconfig:CONFIG_ARCH_CHIP_SH7032]`
- `[Kconfig:CONFIG_ARCH_CHIP_M30262F8]`
- `[Kconfig:CONFIG_ARCH_CHIP_R5F565NEDDFC]`
- `[Kconfig:CONFIG_ARCH_CHIP_R5F565NEHDFC]`
- `[Kconfig:CONFIG_ARCH_CHIP_R5F565NEHDFP]`
- `[Kconfig:CONFIG_ARCH_CHIP_RENESAS_CUSTOM]`
- `[Kconfig:CONFIG_ARCH_SH1]`
- `[Kconfig:CONFIG_ARCH_RENESAS_RX]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[setjmp.h:#error]` Compile-time guard: setjmp() not compiled!
- `[renesas_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[renesas_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[renesas_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[renesas_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[m16c_lowputc.c:#error]` Compile-time configuration constraint: A serial console selected, but corresponding UART not enabled

## Side Effects
- `[renesas_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[renesas_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[renesas_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[m16c_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[m16c_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[m16c_lowputc.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)

## Verification
- Run: `make test`
