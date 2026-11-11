# stm32u5 (`nuttx/arch/arm/src/stm32u5`)

## Overview
Hardware abstraction and architecture package for `stm32u5` (STM32U5 Configuration Options) under `nuttx/arch/arm/src/stm32u5`, providing 12 header file(s) and 10 source file(s) (including `chip.h`, `stm32.h`, `stm32_exti.h`, `stm32_flash.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32u5/hardware`, providing 11 header file(s) and 0 source file(s) (including `stm32_dmasigmap.h`, `stm32_flash.h`, `stm32_i2c.h`, `stm32_memorymap.h`).

## Interface
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:STM32_DMA1_NCHAN]`
- `[chip.h:STM32_DMA1_IRQ_FIRST]`
- `[stm32_exti.h:stm32_gpiosetevent]`
- `[stm32_exti.h:stm32_exti_alarm]`
- `[stm32_exti.h:stm32_exti_wakeup]`
- `[stm32_exti.h:stm32_exti_comp]`
- `[stm32_flash.h:stm32_flash_lock]`
- `[stm32_flash.h:stm32_flash_unlock]`
- `[stm32_flash.h:stm32_flash_user_optbytes]`
- `[stm32_i2c.h:stm32_i2cbus_initialize]`
- `[stm32_i2c.h:stm32_i2cbus_uninitialize]`
- `[stm32_lowputc.h:stm32_lowsetup]`
- `[stm32_mpuinit.h:stm32_mpuinitialize]`
- `[stm32_mpuinit.h:stm32_mpu_uheap]`
- `[stm32_pwr.h:stm32_pwr_enableclk]`
- `[stm32_pwr.h:stm32_pwr_enablebkp]`
- `[stm32_pwr.h:stm32_pwr_adjustvcore]`
- `[stm32_pwr.h:stm32_pwr_enablesmps]`
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
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_rcc_m33.h:#error]` Compile-time guard: Unsupported STM32U5 chip
- `[stm32_dumpgpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_dumpgpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32_dumpgpio.c:#error]` Compile-time configuration constraint: Additional support required for this number of GPIOs
- `[stm32_flash.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_flash.c:#error]` Compile-time configuration constraint: Unrecognized STM32 chip
- `[stm32_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_i2c.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32_lse.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32_lse.c:#error]` Compile-time configuration constraint: Invalid LSE drive capability setting
- `[stm32_mpuinit.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_pwr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[stm32_rcc_m33.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[stm32_rcc_m33.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[stm32_dumpgpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32_flash.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32_flash.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_flash.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32_i2c.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32_i2c.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_i2c.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32_i2c.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[stm32_i2c.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[stm32_i2c.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
