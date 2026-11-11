# misoc (`nuttx/arch/misoc`)

## Overview
Architectural grouping for `nuttx/arch/misoc` (MISOC Peripheral Support), coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/misoc/include`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/misoc/src`, coordinating 3 component subdirectories (`common`, `lm32`, `minerva`).

## Interface
- `[Kconfig:CONFIG_ARCH_CHIP_LM32]`
- `[Kconfig:CONFIG_ARCH_CHIP_MINERVA]`
- `[Kconfig:CONFIG_ARCH_CHIP_MISOC_CUSTOM]`
- `[Kconfig:CONFIG_ARCH_CHIP]`
- `[Kconfig:CONFIG_MISOC_HAVE_UART1]`
- `[Kconfig:CONFIG_MISOC_UART1]`
- `[Kconfig:CONFIG_MISOC_ETHERNET]`
- `[Kconfig:CONFIG_MISOC_UART]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[misoc_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[misoc_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[misoc_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[misoc_net.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[misoc_net.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[misoc_net.c:#error]` Compile-time configuration constraint: High priority work queue support is required

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[misoc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[misoc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[misoc.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[misoc_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[misoc_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
