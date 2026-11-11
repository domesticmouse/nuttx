# risc-v (`nuttx/arch/risc-v`)

## Overview
Architectural grouping for `nuttx/arch/risc-v` (RISC-V Options), coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/risc-v/include`, providing 12 header file(s) and 0 source file(s) (including `arch.h`, `barriers.h`, `csr.h`, `elf.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/risc-v/src`, coordinating 28 component subdirectories (`ab32vg1`, `allwinner-d1`, `bl602`, `bl808`, `c906`, `common`, `eic7700x`, `erbium`, and 20 more).

## Interface
- `[Kconfig:CONFIG_ARCH_CHIP_FE310]`
- `[Kconfig:CONFIG_ARCH_CHIP_K210]`
- `[Kconfig:CONFIG_ARCH_CHIP_LITEX]`
- `[Kconfig:CONFIG_ARCH_CHIP_GD32VW55X]`
- `[Kconfig:CONFIG_ARCH_CHIP_AB32VG1]`
- `[Kconfig:CONFIG_ARCH_CHIP_BL602]`
- `[Kconfig:CONFIG_ARCH_CHIP_ESP32C3_LEGACY]`
- `[Kconfig:CONFIG_ARCH_CHIP_ESP32C2]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[ab32vg1_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ab32vg1_clockconfig.c:#error]` Compile-time configuration constraint: CONFIG_AB32VG1_SYSCLK_MHZ must divide 240 MHz
- `[ab32vg1_gpio.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[ab32vg1_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[ab32vg1_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ab32vg1_serial.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[arch.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[barriers.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[csr.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[syscall.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[ab32vg1_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
