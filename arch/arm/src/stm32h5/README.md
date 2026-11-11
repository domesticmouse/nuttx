# stm32h5 (`nuttx/arch/arm/src/stm32h5`)

## Overview
Hardware abstraction and architecture package for `stm32h5` (STM32H5 Configuration Options; STM32H5 OTP Options) under `nuttx/arch/arm/src/stm32h5`, providing 24 header file(s) and 28 source file(s) (including `chip.h`, `stm32.h`, `stm32_adc.h`, `stm32_capture.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32h5/hardware`, providing 29 header file(s) and 0 source file(s) (including `stm32_adc.h`, `stm32_crc.h`, `stm32_crs.h`, `stm32_dac.h`).

## Interface
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:STM32_DMA1_NCHAN]`
- `[chip.h:STM32_DMA1_IRQ_FIRST]`
- `[chip.h:STM32_DMA2_NCHAN]`
- `[chip.h:STM32_DMA2_IRQ_FIRST]`
- `[chip.h:ARMV8M_ICACHE_LINESIZE]`
- `[chip.h:ARMV8M_DCACHE_LINESIZE]`
- `[stm32_adc.h:stm32_adc_initialize]`
- `[stm32_adc.h:ADC_HAVE_DMA]`
- `[stm32_adc.h:ADC1_HAVE_DMA]`
- `[stm32_adc.h:ADC2_HAVE_DMA]`
- `[stm32_adc.h:ADC_HAVE_OVERSAMPLE]`
- `[stm32_adc.h:ADC1_HAVE_OVERSAMPLE]`
- `[stm32_adc.h:ADC2_HAVE_OVERSAMPLE]`
- `[stm32_adc.h:ADC_HAVE_WDG1]`
- `[stm32_adc.h:ADC_HAVE_WDG2]`
- `[stm32_adc.h:ADC_HAVE_WDG3]`
- `[stm32_adc.h:ADC_HAVE_WDG]`
- `[stm32_adc.h:ADC1_HAVE_TIMER]`
- `[stm32_adc.h:ADC1_TIMER_BASE]`
- `[stm32_capture.h:stm32_cap_init]`
- `[stm32_capture.h:stm32_cap_deinit]`
- `[stm32_capture.h:stm32_cap_initialize]`
- `[stm32_capture.h:stm32_cap_dev_s]`
- `[stm32_capture.h:stm32_cap_ch_cfg_t]`
- `[stm32_capture.h:stm32_cap_smc_cfg_t]`
- `[stm32_capture.h:stm32_cap_flags_t]`
- `[stm32_capture.h:stm32_cap_ops_s]`
- `[stm32_capture.h:STM32_CAP_SETSMC]`
- `[stm32_capture.h:STM32_CAP_SETCLOCK]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_adc.h:#error]` Compile-time guard: CONFIG_STM32_ADC1_SAMPLE_FREQUENCY not defined
- `[stm32_pwm.h:#error]` Compile-time guard: CONFIG_STM32_TIM1_CHANNEL must be provided
- `[stm32_rcc_m33.h:#error]` Compile-time guard: Unsupported STM32H5 chip
- `[stm32_usbdrdhost.h:#error]` Compile-time guard: CONFIG_STM32_USBFS_HOST is required
- `[stm32_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_adc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32_adc.c:#error]` Compile-time configuration constraint: board.h must define STM32_ADC_CLK_FREQUENCY
- `[stm32_capture.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_capture_lowerhalf.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32_dac.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32_dac.c:#error]` Compile-time configuration constraint: DAC1 must be enabled
- `[stm32_dts.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[stm32_rcc_m33.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[stm32_rcc_m33.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[stm32_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32_adc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32_adc.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[stm32_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[stm32_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[stm32_adc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[stm32_capture.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32_capture.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_capture.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
