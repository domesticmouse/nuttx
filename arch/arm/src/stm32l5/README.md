# stm32l5 (`nuttx/arch/arm/src/stm32l5`)

## Overview
Hardware abstraction and architecture package for `stm32l5` (STM32L5 Configuration Options) under `nuttx/arch/arm/src/stm32l5`, providing 8 header file(s) and 9 source file(s) (including `chip.h`, `stm32.h`, `stm32_rcc_m33.h`, `stm32l5_flash.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32l5/hardware`, providing 9 header file(s) and 0 source file(s) (including `stm32_rcc.h`, `stm32l562xx_pinmap.h`, `stm32l562xx_syscfg.h`, `stm32l5_flash.h`).

## Interface
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[stm32_rcc_m33.h:stm32_clockconfig]`
- `[stm32_rcc_m33.h:stm32_board_clockconfig]`
- `[stm32_rcc_m33.h:stm32_stdclockconfig]`
- `[stm32_rcc_m33.h:stm32_clockenable]`
- `[stm32_rcc_m33.h:stm32_rcc_enablelse]`
- `[stm32_rcc_m33.h:stm32_rcc_enablelsi]`
- `[stm32_rcc_m33.h:stm32_rcc_disablelsi]`
- `[stm32_rcc_m33.h:stm32_rcc_enableperipherals]`
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
- `[stm32l5_flash.h:stm32_flash_lock]`
- `[stm32l5_flash.h:stm32_flash_unlock]`
- `[stm32l5_flash.h:stm32_flash_user_optbytes]`
- `[stm32l5_mpuinit.h:stm32_mpuinitialize]`
- `[stm32l5_mpuinit.h:stm32_mpu_uheap]`
- `[stm32l5_pwr.h:stm32_pwr_enableclk]`
- `[stm32l5_pwr.h:stm32_pwr_enablebkp]`
- `[stm32l5_pwr.h:stm32_pwr_enableusv]`
- `[stm32l5_pwr.h:stm32_pwr_vddio2_valid]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_rcc_m33.h:#error]` Compile-time guard: Unsupported STM32L5 chip
- `[stm32l562xx_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32l562xx_rcc.c:#error]` Compile-time configuration constraint: stm32_stdclockconfig(), must have one of STM32_BOARD_USEHSI, STM32_BOARD_USEMSI, STM32_BOARD_USEHSE 
- `[stm32l5_dumpgpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32l5_dumpgpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32l5_dumpgpio.c:#error]` Compile-time configuration constraint: Additional support required for this number of GPIOs
- `[stm32l5_flash.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32l5_flash.c:#error]` Compile-time configuration constraint: Unrecognized STM32 chip
- `[stm32l5_lse.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32l5_lse.c:#error]` Compile-time configuration constraint: Invalid LSE drive capability setting
- `[stm32l5_mpuinit.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32l5_rcc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`

## Side Effects
- `[stm32_rcc_m33.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[stm32_rcc_m33.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[stm32l562xx_rcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32l562xx_rcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32l5_dumpgpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32l5_flash.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32l5_flash.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32l5_flash.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32l5_lse.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32l5_lse.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32l5_pwr.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32l5_pwr.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
