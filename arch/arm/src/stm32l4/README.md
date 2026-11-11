# stm32l4 (`nuttx/arch/arm/src/stm32l4`)

## Overview
Hardware abstraction and architecture package for `stm32l4` (STM32L4 Configuration Options; STM32L4 SRAM2 and SRAM3 Options) under `nuttx/arch/arm/src/stm32l4`, providing 33 header file(s) and 52 source file(s) (including `chip.h`, `stm32.h`, `stm32l4_adc.h`, `stm32l4_can.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32l4/hardware`, providing 46 header file(s) and 0 source file(s) (including `stm32_rcc.h`, `stm32l4_adc.h`, `stm32l4_can.h`, `stm32l4_comp.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV7M_DCACHE_LINESIZE]`
- `[chip.h:ARMV7M_ICACHE_LINESIZE]`
- `[stm32l4_adc.h:stm32_adc_initialize]`
- `[stm32l4_adc.h:stm32_adc_dev_s]`
- `[stm32l4_adc.h:stm32_adc_ops_s]`
- `[stm32l4_adc.h:ADC_HAVE_DFSDM]`
- `[stm32l4_adc.h:ADC1_HAVE_DFSDM]`
- `[stm32l4_adc.h:ADC2_HAVE_DFSDM]`
- `[stm32l4_adc.h:ADC3_HAVE_DFSDM]`
- `[stm32l4_adc.h:ADC_HAVE_DMA]`
- `[stm32l4_adc.h:ADC1_HAVE_DMA]`
- `[stm32l4_adc.h:ADC2_HAVE_DMA]`
- `[stm32l4_adc.h:ADC3_HAVE_DMA]`
- `[stm32l4_adc.h:ADC_HAVE_INJECTED]`
- `[stm32l4_adc.h:ADC1_HAVE_TIMER]`
- `[stm32l4_adc.h:ADC1_TIMER_BASE]`
- `[stm32l4_adc.h:ADC1_TIMER_PCLK_FREQUENCY]`
- `[stm32l4_can.h:stm32_caninitialize]`
- `[stm32l4_can.h:CONFIG_STM32_CAN_TSEG1]`
- `[stm32l4_can.h:CONFIG_STM32_CAN_TSEG2]`
- `[stm32l4_comp.h:stm32_compinitialize]`
- `[stm32l4_comp.h:stm32_comp_e]`
- `[stm32l4_comp.h:stm32_comp_inp_e]`
- `[stm32l4_comp.h:stm32_comp_inm_e]`
- `[stm32l4_comp.h:stm32_comp_hyst_e]`
- `[stm32l4_comp.h:stm32_comp_speed_e]`
- `[stm32l4_comp.h:stm32_comp_config_s]`
- `[stm32l4_dac.h:stm32_dacinitialize]`
- `[stm32l4_dac.h:stm32_dac_dev_s]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32l4_adc.h:#error]` Compile-time guard: CONFIG_STM32_ADC1_SAMPLE_FREQUENCY not defined
- `[stm32l4_can.h:#error]` Compile-time guard: CONFIG_STM32_CAN1_BAUD is not defined
- `[stm32l4_dfsdm.h:#error]` Compile-time guard: CONFIG_STM32_DFSDM_SAMPLE_FREQUENCY not defined
- `[stm32l4_dma.h:#error]` Compile-time guard: Unsupported STM32L4 chip
- `[stm32l4_firewall.h:#error]` Compile-time guard: Unsupported STM32L4 chip
- `[stm32l4_gpio.h:#error]` Compile-time guard: Unsupported STM32L4 chip
- `[stm32l4_otgfs.h:#error]` Compile-time guard: Unsupported STM32L4 chip
- `[stm32l4_pwm.h:#error]` Compile-time guard: CONFIG_STM32_TIM1_CHANNEL must be provided
- `[stm32l4_rcc.h:#error]` Compile-time guard: Unsupported STM32L4 chip
- `[stm32l4_uart.h:#error]` Compile-time guard: Unsupported STM32L4 chip
- `[stm32l4_usbhost.h:#error]` Compile-time guard: Unsupported STM32L4 chip
- `[stm32l4_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[stm32l4_rcc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[stm32l4_rcc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[stm32l4_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32l4_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32l4_adc.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[stm32l4_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[stm32l4_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[stm32l4_adc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[stm32l4_can.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32l4_can.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32l4_can.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[stm32l4_can.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
