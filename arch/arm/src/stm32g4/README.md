# stm32g4 (`nuttx/arch/arm/src/stm32g4`)

## Overview
Hardware abstraction and architecture package for `stm32g4` (STM32 G4 configuration) under `nuttx/arch/arm/src/stm32g4`, providing 2 header file(s) and 2 source file(s) (including `chip.h`, `stm32.h`, `stm32_rcc.c`, `stm32g4xxxx_rcc.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32g4/hardware`, providing 21 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32g47xxx_hrtim.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[stm32_rcc.c:stm32_clockconfig]`
- `[stm32_rcc.c:stm32_clockenable]`
- `[stm32g4xxxx_rcc.c:rcc_reset]`
- `[stm32g4xxxx_rcc.c:USE_HSE]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G431K]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G431C]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G431R]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G431M]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G431V]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G474C]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G474M]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G474R]`
- `[Make.defs:CHIP_CSRCS]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32g4xxxx_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32g4xxxx_rcc.c:#error]` Compile-time configuration constraint: STM32_SYSCLK_SW is RCC_CFGR_SW_PLL but STM32_PLLCFGR_PLLSRC is not recognized!

## Side Effects
- `[stm32_rcc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32g4xxxx_rcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32g4xxxx_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
