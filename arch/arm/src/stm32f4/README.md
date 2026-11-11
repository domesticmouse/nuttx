# stm32f4 (`nuttx/arch/arm/src/stm32f4`)

## Overview
Hardware abstraction and architecture package for `stm32f4` (STM32 F4 configuration) under `nuttx/arch/arm/src/stm32f4`, providing 2 header file(s) and 2 source file(s) (including `chip.h`, `stm32.h`, `stm32_rcc.c`, `stm32f40xxx_rcc.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32f4/hardware`, providing 8 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32f40xxx_gpio.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[stm32_rcc.c:stm32_clockconfig]`
- `[stm32_rcc.c:stm32_clockenable]`
- `[stm32f40xxx_rcc.c:rcc_reset]`
- `[stm32f40xxx_rcc.c:HSERDY_TIMEOUT]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F401CB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F401RB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F401VB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F401CC]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F401RC]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F401VC]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F401CD]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F401RD]`
- `[Make.defs:CHIP_CSRCS]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32f40xxx_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32f40xxx_rcc.c:#error]` Compile-time configuration constraint: STM32_SYSCLK_FREQUENCY is out of range!

## Side Effects
- `[stm32_rcc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32f40xxx_rcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32f40xxx_rcc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32f40xxx_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
