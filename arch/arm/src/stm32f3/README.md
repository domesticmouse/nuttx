# stm32f3 (`nuttx/arch/arm/src/stm32f3`)

## Overview
Hardware abstraction and architecture package for `stm32f3` (STM32 F3 configuration) under `nuttx/arch/arm/src/stm32f3`, providing 2 header file(s) and 4 source file(s) (including `chip.h`, `stm32.h`, `stm32_rcc.c`, `stm32f30xxx_rcc.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32f3/hardware`, providing 20 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32f30xxx_gpio.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[stm32_rcc.c:stm32_clockconfig]`
- `[stm32_rcc.c:stm32_clockenable]`
- `[stm32f30xxx_rcc.c:rcc_reset]`
- `[stm32f30xxx_rcc.c:HSERDY_TIMEOUT]`
- `[stm32f33xxx_rcc.c:rcc_reset]`
- `[stm32f33xxx_rcc.c:HSERDY_TIMEOUT]`
- `[stm32f37xxx_rcc.c:rcc_reset]`
- `[stm32f37xxx_rcc.c:HSERDY_TIMEOUT]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F302K6]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F302K8]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F302C6]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F302C8]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F302R6]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F302R8]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F302CB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F302CC]`
- `[Make.defs:CHIP_CSRCS]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32_rcc.c:#error]` Compile-time configuration constraint: Unsupported STM32F3 chip
- `[stm32f30xxx_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32f30xxx_rcc.c:#error]` Compile-time configuration constraint: STM32_SYSCLK_FREQUENCY is out of range!
- `[stm32f33xxx_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32f33xxx_rcc.c:#error]` Compile-time configuration constraint: STM32_SYSCLK_FREQUENCY is out of range!
- `[stm32f37xxx_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32f37xxx_rcc.c:#error]` Compile-time configuration constraint: STM32_SYSCLK_FREQUENCY is out of range!

## Side Effects
- `[stm32_rcc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32f30xxx_rcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32f30xxx_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32f33xxx_rcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32f33xxx_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32f37xxx_rcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32f37xxx_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
