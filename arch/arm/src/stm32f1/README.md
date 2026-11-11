# stm32f1 (`nuttx/arch/arm/src/stm32f1`)

## Overview
Hardware abstraction and architecture package for `stm32f1` (STM32 F1 configuration; Alternate Pin Mapping) under `nuttx/arch/arm/src/stm32f1`, providing 2 header file(s) and 2 source file(s) (including `chip.h`, `stm32.h`, `stm32_rcc.c`, `stm32f10xxx_rcc.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32f1/hardware`, providing 14 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32f100_pinmap.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[stm32_rcc.c:stm32_clockconfig]`
- `[stm32_rcc.c:stm32_clockenable]`
- `[stm32f10xxx_rcc.c:rcc_reset]`
- `[stm32f10xxx_rcc.c:HSERDY_TIMEOUT]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F100C8]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F100CB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F100R8]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F100RB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F100RC]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F100RD]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F100RE]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32F100V8]`
- `[Kconfig.pinmap:CONFIG_STM32_CAN1_NO_REMAP]`
- `[Kconfig.pinmap:CONFIG_STM32_CAN1_REMAP1]`
- `[Kconfig.pinmap:CONFIG_STM32_CAN1_REMAP2]`
- `[Kconfig.pinmap:CONFIG_STM32_CAN2_REMAP]`
- `[Kconfig.pinmap:CONFIG_STM32_CEC_REMAP]`
- `[Kconfig.pinmap:CONFIG_STM32_ETH_REMAP]`
- `[Kconfig.pinmap:CONFIG_STM32_I2C1_REMAP]`
- `[Kconfig.pinmap:CONFIG_STM32_SPI1_REMAP]`
- `[Make.defs:CHIP_CSRCS]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32f10xxx_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32f10xxx_rcc.c:#error]` Compile-time configuration constraint: STM32_SYSCLK_FREQUENCY is out of range!

## Side Effects
- `[stm32_rcc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32f10xxx_rcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32f10xxx_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
