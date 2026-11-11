# stm32f2 (`nuttx/arch/arm/src/stm32f2`)

## Overview
Hardware abstraction and architecture package for `stm32f2` (STM32 F2 configuration) under `nuttx/arch/arm/src/stm32f2`, providing 2 header file(s) and 2 source file(s) (including `chip.h`, `stm32.h`, `stm32_rcc.c`, `stm32f20xxx_rcc.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32f2/hardware`, providing 7 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32f20xxx_gpio.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[stm32_rcc.c:stm32_clockconfig]`
- `[stm32_rcc.c:stm32_clockenable]`
- `[stm32f20xxx_rcc.c:rcc_reset]`
- `[stm32f20xxx_rcc.c:HSERDY_TIMEOUT]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F205RG]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F207VC]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F207VE]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F207VF]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F207VG]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F207IC]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F207IE]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F207IF]`
- `[Make.defs:CHIP_CSRCS]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32f20xxx_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32f20xxx_rcc.c:#error]` Compile-time configuration constraint: STM32_SYSCLK_FREQUENCY is out of range!

## Side Effects
- `[stm32_rcc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32f20xxx_rcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32f20xxx_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
