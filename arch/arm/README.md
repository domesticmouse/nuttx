# arm (`nuttx/arch/arm`)

## Overview
Architectural grouping for `nuttx/arch/arm` (ARM Options), coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/arm/include`, providing 10 header file(s) and 0 source file(s) (including `arch.h`, `barriers.h`, `elf.h`, `inttypes.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/arm/src`, coordinating 94 component subdirectories (`a1x`, `am335x`, `am67`, `arm`, `armv6-m`, `armv7-a`, `armv7-m`, `armv7-r`, and 86 more).

## Interface
- `[Kconfig:CONFIG_ARM_TOOLCHAIN_IAR]`
- `[Kconfig:CONFIG_ARM_TOOLCHAIN_BUILDROOT]`
- `[Kconfig:CONFIG_ARM_TOOLCHAIN_BUILDROOT_OABI]`
- `[Kconfig:CONFIG_ARM_TOOLCHAIN_GNU_EABI]`
- `[Kconfig:CONFIG_ARM_TOOLCHAIN_GNU_OABI]`
- `[Kconfig:CONFIG_ARM_TOOLCHAIN_CLANG]`
- `[Kconfig:CONFIG_ARM_TOOLCHAIN_ARMCLANG]`
- `[Kconfig:CONFIG_ARM_TOOLCHAIN_GHS]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[arch.h:#error]` Compile-time guard: Only pages sizes of 4096 are currently supported (CONFIG_ARCH_ADDRENV)
- `[a1x_boot.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a1x_boot.c:#error]` Compile-time configuration constraint: High vector remap cannot be performed if we are using a ROM page table
- `[a1x_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a1x_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[a1x_lowputc.c:#error]` Compile-time configuration constraint: No CONFIG_UARTn_SERIAL_CONSOLE Setting

## Side Effects
- `[arch.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[syscall.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[a1x_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a1x_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[a1x_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[a1x_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
