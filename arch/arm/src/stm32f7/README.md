# stm32f7 (`nuttx/arch/arm/src/stm32f7`)

## Overview
Hardware abstraction and architecture package for `stm32f7` (STM32 F7 Configuration Options) under `nuttx/arch/arm/src/stm32f7`, providing 35 header file(s) and 49 source file(s) (including `chip.h`, `stm32.h`, `stm32_adc.h`, `stm32_alarm.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32f7/hardware`, providing 55 header file(s) and 0 source file(s) (including `stm32_adc.h`, `stm32_can.h`, `stm32_dma.h`, `stm32_dma2d.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV7M_DCACHE_LINESIZE]`
- `[chip.h:ARMV7M_ICACHE_LINESIZE]`
- `[stm32_adc.h:stm32_adc_initialize]`
- `[stm32_adc.h:adc_io_cmds_e]`
- `[stm32_adc.h:stm32_adc_resoluton_e]`
- `[stm32_adc.h:stm32_adc_multimode_e]`
- `[stm32_adc.h:adc_channel_t]`
- `[stm32_adc.h:adc_sample_time_s]`
- `[stm32_adc.h:stm32_adc_dev_s]`
- `[stm32_adc.h:stm32_adc_ops_s]`
- `[stm32_adc.h:STM32_ADC_DMAREG_OFFSET]`
- `[stm32_adc.h:ADC_DMAREG_DMA]`
- `[stm32_adc.h:STM32_ADC_EXTREG_OFFSET]`
- `[stm32_adc.h:ADC_EXTREG_EXTSEL_MASK]`
- `[stm32_adc.h:ADC_EXTREG_EXTSEL_SHIFT]`
- `[stm32_adc.h:STM32_ADC_JEXTREG_OFFSET]`
- `[stm32_adc.h:ADC_JEXTREG_JEXTSEL_MASK]`
- `[stm32_adc.h:ADC_EXTREG_JEXTSEL_SHIFT]`
- `[stm32_adc.h:STM32_ADC_ISR_OFFSET]`
- `[stm32_adc.h:STM32_ADC_IER_OFFSET]`
- `[stm32_adc.h:ADC_EXTREG_EXTEN_MASK]`
- `[stm32_adc.h:ADC_EXTREG_EXTEN_NONE]`
- `[stm32_alarm.h:stm32_rtc_setalarm]`
- `[stm32_alarm.h:stm32_rtc_rdalarm]`
- `[stm32_alarm.h:stm32_rtc_cancelalarm]`
- `[stm32_alarm.h:stm32_rtc_setperiodic]`
- `[stm32_alarm.h:stm32_rtc_cancelperiodic]`
- `[stm32_alarm.h:alm_id_e]`
- `[stm32_alarm.h:alm_setalarm_s]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_adc.h:#error]` Compile-time guard: CONFIG_STM32_ADC1_SAMPLE_FREQUENCY not defined
- `[stm32_bbsram.h:#error]` Compile-time guard: No backup SRAM on this STM32 Device
- `[stm32_can.h:#error]` Compile-time guard: CONFIG_STM32_CAN1_BAUD is not defined
- `[stm32_pwm.h:#error]` Compile-time guard: CONFIG_STM32_TIM1_CHANNEL must be provided
- `[stm32_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_adc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32_adc.c:#error]` Compile-time configuration constraint: PCLK2 too high - no divisor found 
- `[stm32_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_allocateheap.c:#error]` Compile-time configuration constraint: CONFIG_ARCH_HAVE_HEAP2 but not CONFIG_STM32_FMC! Kconfig flawed?
- `[stm32_bbsram.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_bbsram.c:#error]` Compile-time configuration constraint: Driver Requires CONFIG_STM32_BKPSRAM to be enabled
- `[stm32_can.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

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
- `[stm32_adc.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[stm32_can.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32_can.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
