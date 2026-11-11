# stm32l0 (`nuttx/arch/arm/src/stm32l0`)

## Overview
Hardware abstraction and architecture package for `stm32l0` (STM32 L0 configuration) under `nuttx/arch/arm/src/stm32l0`, providing 2 header file(s) and 2 source file(s) (including `chip.h`, `stm32.h`, `stm32_rcc.c`, `stm32l0_rcc.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32l0/hardware`, providing 9 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32l0_exti.h`).

## Interface
- `[stm32_rcc.c:stm32_clockconfig]`
- `[stm32_rcc.c:stm32_clockenable]`
- `[stm32l0_rcc.c:rcc_reset]`
- `[stm32l0_rcc.c:HSERDY_TIMEOUT]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L053C8]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L053R8]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L071K8]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L071KB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L071KZ]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L071C8]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L071CB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32L071CZ]`
- `[Make.defs:CHIP_CSRCS]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32_rcc.c:#error]` Compile-time configuration constraint: RNG requires CLK48 enabled
- `[stm32l0_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32l0_rcc.c:#error]` Compile-time configuration constraint: VREFINT must be enabled if HSI48 used

## Side Effects
- `[stm32_rcc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32l0_rcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32l0_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32l0_rcc.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)

## Verification
- Run: `make test`
