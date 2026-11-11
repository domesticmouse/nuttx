# stm32h7 (`nuttx/arch/arm/src/stm32h7`)

## Overview
Hardware abstraction and architecture package for `stm32h7` (STM32 H7 Configuration Options; Application Image Configuration) under `nuttx/arch/arm/src/stm32h7`, providing 40 header file(s) and 55 source file(s) (including `chip.h`, `stm32.h`, `stm32_adc.h`, `stm32_aes.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32h7/hardware`, providing 51 header file(s) and 0 source file(s) (including `stm32_adc.h`, `stm32_axi.h`, `stm32_bdma.h`, `stm32_dac.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV7M_DCACHE_LINESIZE]`
- `[chip.h:ARMV7M_ICACHE_LINESIZE]`
- `[stm32_adc.h:stm32_adc_initialize]`
- `[stm32_adc.h:ADC_HAVE_DFSDM]`
- `[stm32_adc.h:ADC1_HAVE_DFSDM]`
- `[stm32_adc.h:ADC2_HAVE_DFSDM]`
- `[stm32_adc.h:ADC3_HAVE_DFSDM]`
- `[stm32_adc.h:ADC_HAVE_DMA]`
- `[stm32_adc.h:ADC1_HAVE_DMA]`
- `[stm32_adc.h:ADC2_HAVE_DMA]`
- `[stm32_adc.h:ADC3_HAVE_DMA]`
- `[stm32_adc.h:ADC1_HAVE_TIMER]`
- `[stm32_adc.h:ADC1_TIMER_BASE]`
- `[stm32_adc.h:ADC1_TIMER_PCLK_FREQUENCY]`
- `[stm32_adc.h:ADC1_TIMER_RCC_ENR]`
- `[stm32_alarm.h:stm32_rtc_setalarm]`
- `[stm32_alarm.h:stm32_rtc_rdalarm]`
- `[stm32_alarm.h:stm32_rtc_cancelalarm]`
- `[stm32_alarm.h:stm32_rtc_setperiodic]`
- `[stm32_alarm.h:stm32_rtc_cancelperiodic]`
- `[stm32_alarm.h:alm_id_e]`
- `[stm32_alarm.h:alm_setalarm_s]`
- `[stm32_alarm.h:alm_rdalarm_s]`
- `[stm32_bbsram.h:stm32_bbsraminitialize]`
- `[stm32_bbsram.h:stm32_bbsram_savepanic]`
- `[stm32_bbsram.h:bbsramdf_e]`
- `[stm32_bbsram.h:bbsramd_s]`
- `[stm32_bbsram.h:STM32_BBSRAM_SIZE]`
- `[stm32_bbsram.h:CONFIG_STM32_BBSRAM_FILES]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_adc.h:#error]` Compile-time guard: CONFIG_STM32_ADC1_SAMPLE_FREQUENCY not defined
- `[stm32_aes.h:#error]` Compile-time guard: Unknown chip for AES
- `[stm32_otg.h:#error]` Compile-time guard: board.h selected HSI48 as USB clock source, but HSI48 is not \
- `[stm32_pwm.h:#error]` Compile-time guard: CONFIG_STM32_TIM1_CHANNEL must be provided
- `[stm32_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_adc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32_adc.c:#error]` Compile-time configuration constraint: STM32H7 ADC DMA support requires CONFIG_STM32_DMA1 or CONFIG_STM32_DMA2
- `[stm32_aes.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_bbsram.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_bbsram.c:#error]` Compile-time configuration constraint: Driver Requires CONFIG_STM32_BKPSRAM to be enabled
- `[stm32_capture.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[stm32_rcc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[stm32_rcc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[stm32_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32_adc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32_adc.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[stm32_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[stm32_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[stm32_adc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[stm32_aes.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32_aes.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32_capture.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
