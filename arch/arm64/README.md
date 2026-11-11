# arm64 (`nuttx/arch/arm64`)

## Overview
Architectural grouping for `nuttx/arch/arm64` (ARM64 Options; ARMv8.5 architectural features), coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/arm64/include`, providing 10 header file(s) and 0 source file(s) (including `arch.h`, `barriers.h`, `elf.h`, `inttypes.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/arm64/src`, coordinating 13 component subdirectories (`a527`, `a64`, `am62x`, `bcm2711`, `common`, `fvp-v8r`, `goldfish`, `imx8`, and 5 more).

## Interface
- `[Kconfig:CONFIG_ARM64_TOOLCHAIN_GNU_EABI]`
- `[Kconfig:CONFIG_ARM64_TOOLCHAIN_CLANG]`
- `[Kconfig:CONFIG_ARCH_CHIP_AM62X]`
- `[Kconfig:CONFIG_ARCH_CHIP_A64]`
- `[Kconfig:CONFIG_ARCH_CHIP_RK3399]`
- `[Kconfig:CONFIG_ARCH_CHIP_RK3588]`
- `[Kconfig:CONFIG_ARCH_CHIP_QEMU]`
- `[Kconfig:CONFIG_ARCH_CHIP_GOLDFISH]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[irq.h:#error]` Compile-time guard: ARM64_CONTEXT_REGS and FPU_CONTEXT_REGS must be an even number to ensure the stack is aligned to 16 
- `[a527_boot.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[a64_de.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a64_mipi_dsi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a64_pio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a64_pio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[arch.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[barriers.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[syscall.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[a64_de.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a64_de.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
