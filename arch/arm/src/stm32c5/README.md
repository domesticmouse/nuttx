# stm32c5 (`nuttx/arch/arm/src/stm32c5`)

## Overview
Hardware abstraction and architecture package for `stm32c5` (STM32C5 Configuration Options) under `nuttx/arch/arm/src/stm32c5`, providing 3 header file(s) and 2 source file(s) (including `chip.h`, `stm32.h`, `stm32_rcc_m33.h`, `stm32_rcc.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32c5/hardware`, providing 9 header file(s) and 0 source file(s) (including `stm32_dmasigmap.h`, `stm32_flash.h`, `stm32_memorymap.h`, `stm32_pinmap.h`).

## Interface
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:STM32_DMA1_NCHAN]`
- `[chip.h:STM32_DMA1_IRQ_FIRST]`
- `[chip.h:STM32_DMA2_NCHAN]`
- `[chip.h:STM32_DMA2_IRQ_FIRST]`
- `[stm32_rcc_m33.h:stm32_clockconfig]`
- `[stm32_rcc_m33.h:stm32_board_clockconfig]`
- `[stm32_rcc_m33.h:stm32_stdclockconfig]`
- `[stm32_rcc_m33.h:stm32_clockenable]`
- `[stm32_rcc_m33.h:stm32_rcc_enableperipherals]`
- `[stm32_rcc_m33.h:stm32_rcc_enablelsi]`
- `[stm32_rcc_m33.h:stm32_rcc_disablelsi]`
- `[stm32_rcc_m33.h:STM32_LPUART1_FREQUENCY]`
- `[stm32_rcc_m33.h:STM32_LPUART1_RCC_REG]`
- `[stm32_rcc_m33.h:STM32_LPUART1_RCC_EN]`
- `[stm32_rcc_m33.h:STM32_USART1_FREQUENCY]`
- `[stm32_rcc_m33.h:STM32_USART1_RCC_REG]`
- `[stm32_rcc_m33.h:STM32_USART1_RCC_EN]`
- `[stm32_rcc_m33.h:STM32_USART2_FREQUENCY]`
- `[stm32_rcc_m33.h:STM32_USART2_RCC_REG]`
- `[stm32_rcc_m33.h:STM32_USART2_RCC_EN]`
- `[stm32_rcc_m33.h:STM32_USART3_FREQUENCY]`
- `[stm32_rcc_m33.h:STM32_USART3_RCC_REG]`
- `[stm32_rcc_m33.h:STM32_USART3_RCC_EN]`
- `[stm32_rcc.c:stm32_clockconfig]`
- `[stm32_rcc.c:stm32_clockenable]`
- `[stm32c5xx_rcc.c:stm32_stdclockconfig]`
- `[stm32c5xx_rcc.c:stm32_rcc_enableperipherals]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_STM32_C5_PERIPHERALS]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32c5xx_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32c5xx_rcc.c:#error]` Compile-time configuration constraint: stm32_stdclockconfig() requires HSE and PSI board configuration

## Side Effects
- `[stm32c5xx_rcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32c5xx_rcc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32c5xx_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
