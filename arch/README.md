# arch (`nuttx/arch`)

## Overview
Architecture-specific Hardware Abstraction Layer (HAL) root for Apache NuttX, organizing processor families, chip-level peripheral drivers, interrupt controllers, context-switching routines, and boot/linker infrastructure across 18 CPU architectures.

## Subdirectories & Boundaries
- `arm`: [./arm/README.md](./arm/README.md) - Architectural grouping for `nuttx/arch/arm` (ARM Options), coordinating 2 component subdirectories (`include`, `src`).
- `arm64`: [./arm64/README.md](./arm64/README.md) - Architectural grouping for `nuttx/arch/arm64` (ARM64 Options; ARMv8.5 architectural features), coordinating 2 component subdirectories (`include`, `src`).
- `avr`: [./avr/README.md](./avr/README.md) - Architectural grouping for `nuttx/arch/avr`, coordinating 2 component subdirectories (`include`, `src`).
- `ceva`: [./ceva/README.md](./ceva/README.md) - Architectural grouping for `nuttx/arch/ceva` (CEVA Options), coordinating 2 component subdirectories (`include`, `src`).
- `hc`: [./hc/README.md](./hc/README.md) - Architectural grouping for `nuttx/arch/hc`, coordinating 2 component subdirectories (`include`, `src`).
- `mips`: [./mips/README.md](./mips/README.md) - Architectural grouping for `nuttx/arch/mips`, coordinating 2 component subdirectories (`include`, `src`).
- `misoc`: [./misoc/README.md](./misoc/README.md) - Architectural grouping for `nuttx/arch/misoc` (MISOC Peripheral Support), coordinating 2 component subdirectories (`include`, `src`).
- `or1k`: [./or1k/README.md](./or1k/README.md) - Architectural grouping for `nuttx/arch/or1k` (OpenRISC Options), coordinating 2 component subdirectories (`include`, `src`).
- `renesas`: [./renesas/README.md](./renesas/README.md) - Architectural grouping for `nuttx/arch/renesas`, coordinating 2 component subdirectories (`include`, `src`).
- `risc-v`: [./risc-v/README.md](./risc-v/README.md) - Architectural grouping for `nuttx/arch/risc-v` (RISC-V Options), coordinating 2 component subdirectories (`include`, `src`).
- `sim`: [./sim/README.md](./sim/README.md) - Architectural grouping for `nuttx/arch/sim` (Simulation Configuration Options; Simulated v4l2m2m support), coordinating 2 component subdirectories (`include`, `src`).
- `sparc`: [./sparc/README.md](./sparc/README.md) - Architectural grouping for `nuttx/arch/sparc`, coordinating 2 component subdirectories (`include`, `src`).
- `tricore`: [./tricore/README.md](./tricore/README.md) - Architectural grouping for `nuttx/arch/tricore` (Tricore Options), coordinating 2 component subdirectories (`include`, `src`).
- `x86`: [./x86/README.md](./x86/README.md) - Architectural grouping for `nuttx/arch/x86` (x86 Configuration Options), coordinating 2 component subdirectories (`include`, `src`).
- `x86_64`: [./x86_64/README.md](./x86_64/README.md) - Architectural grouping for `nuttx/arch/x86_64` (x86_64 Configuration Options), coordinating 2 component subdirectories (`include`, `src`).
- `xtensa`: [./xtensa/README.md](./xtensa/README.md) - Architectural grouping for `nuttx/arch/xtensa`, coordinating 2 component subdirectories (`include`, `src`).
- `z16`: [./z16/README.md](./z16/README.md) - Architectural grouping for `nuttx/arch/z16` (Z16 Configuration Options), coordinating 2 component subdirectories (`include`, `src`).
- `z80`: [./z80/README.md](./z80/README.md) - Architectural grouping for `nuttx/arch/z80`, coordinating 2 component subdirectories (`include`, `src`).

## Interface
- `[CMakeLists.txt:nuttx_add_kernel_library]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_ARM]`
- `[Kconfig:CONFIG_ARCH_ARM64]`
- `[Kconfig:CONFIG_ARCH_AVR]`
- `[Kconfig:CONFIG_ARCH_HC]`
- `[Kconfig:CONFIG_ARCH_MIPS]`
- `[Kconfig:CONFIG_ARCH_MISOC]`
- `[Kconfig:CONFIG_ARCH_RENESAS]`
- `[Kconfig:CONFIG_ARCH_RISCV]`
- [./arm/README.md](./arm/README.md)
- [./arm64/README.md](./arm64/README.md)
- [./avr/README.md](./avr/README.md)
- [./ceva/README.md](./ceva/README.md)
- [./hc/README.md](./hc/README.md)
- [./mips/README.md](./mips/README.md)
- [./misoc/README.md](./misoc/README.md)
- [./or1k/README.md](./or1k/README.md)
- [./renesas/README.md](./renesas/README.md)
- [./risc-v/README.md](./risc-v/README.md)
- [./sim/README.md](./sim/README.md)
- [./sparc/README.md](./sparc/README.md)
- [./tricore/README.md](./tricore/README.md)
- [./x86/README.md](./x86/README.md)
- [./x86_64/README.md](./x86_64/README.md)
- [./xtensa/README.md](./xtensa/README.md)
- [./z16/README.md](./z16/README.md)
- [./z80/README.md](./z80/README.md)

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
