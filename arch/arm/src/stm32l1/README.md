# stm32l1 (`nuttx/arch/arm/src/stm32l1`)

## Overview
Hardware abstraction and architecture package for `stm32l1` (STM32 L1 configuration) under `nuttx/arch/arm/src/stm32l1`, providing 2 header file(s) and 2 source file(s) (including `chip.h`, `stm32.h`, `stm32_rcc.c`, `stm32l15xxx_rcc.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32l1/hardware`, providing 8 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32l15xxx_aes.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[stm32_rcc.c:stm32_clockconfig]`
- `[stm32_rcc.c:stm32_clockenable]`
- `[stm32l15xxx_rcc.c:rcc_reset]`
- `[stm32l15xxx_rcc.c:HSERDY_TIMEOUT]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L151C6]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L151C8]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L151CB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L151R6]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L151R8]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L151RB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L151V6]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L151V8]`
- `[Make.defs:CHIP_CSRCS]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32l15xxx_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`

## Side Effects
- `[stm32_rcc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32l15xxx_rcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32l15xxx_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32l15xxx_rcc.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)

## Verification
- Run: `make test`
