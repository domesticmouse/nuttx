# stm32g0 (`nuttx/arch/arm/src/stm32g0`)

## Overview
Hardware abstraction and architecture package for `stm32g0` (STM32 G0 configuration) under `nuttx/arch/arm/src/stm32g0`, providing 2 header file(s) and 2 source file(s) (including `chip.h`, `stm32.h`, `stm32_rcc.c`, `stm32g0_rcc.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32g0/hardware`, providing 10 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32g0_dmamux.h`).

## Interface
- `[stm32_rcc.c:stm32_clockconfig]`
- `[stm32_rcc.c:stm32_clockenable]`
- `[stm32g0_rcc.c:rcc_reset]`
- `[stm32g0_rcc.c:HSERDY_TIMEOUT]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G070CB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G070KB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G070RB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G071EB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G071G8]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G071GB]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G071G8XN]`
- `[Kconfig:CONFIG_ARCH_CHIP_STM32G071GBXN]`
- `[Make.defs:CHIP_CSRCS]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32.h:#error]` Compile-time guard: FDCAN1 cannot be used with TIM16 or TIM17
- `[stm32_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32_rcc.c:#error]` Compile-time configuration constraint: RNG requires CLK48 enabled
- `[stm32g0_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`

## Side Effects
- `[stm32_rcc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32g0_rcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32g0_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32g0_rcc.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)

## Verification
- Run: `make test`
