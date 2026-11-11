# stm32 (`nuttx/arch/arm/src/common/stm32`)

## Overview
Hardware abstraction and architecture package for `stm32` (STM32 Configuration Options; ADC Configuration) under `nuttx/arch/arm/src/common/stm32`, providing 95 header file(s) and 132 source file(s) (including `stm32_1wire.h`, `stm32_adc.h`, `stm32_adc_m0_v1.h`, `stm32_adc_m3m4_v1v2.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/common/stm32/hardware`, providing 91 header file(s) and 0 source file(s) (including `stm32_adc.h`, `stm32_adc_v1.h`, `stm32_adc_v1l1.h`, `stm32_adc_v2.h`).

## Interface
- `[stm32_1wire.h:stm32_1wireinitialize]`
- `[stm32_1wire.h:stm32_1wireuninitialize]`
- `[stm32_adc_m0_v1.h:stm32_adcinitialize]`
- `[stm32_adc_m0_v1.h:stm32_adc_llops_get]`
- `[stm32_adc_m0_v1.h:adc_io_cmds_e]`
- `[stm32_adc_m0_v1.h:stm32_adc_resoluton_e]`
- `[stm32_adc_m0_v1.h:adc_sample_time_s]`
- `[stm32_adc_m0_v1.h:stm32_adc_dev_s]`
- `[stm32_adc_m0_v1.h:stm32_adc_ops_s]`
- `[stm32_adc_m0_v1.h:ADC_HAVE_DMA]`
- `[stm32_adc_m0_v1.h:ADC1_HAVE_DMA]`
- `[stm32_adc_m0_v1.h:ADC1_HAVE_TIMER]`
- `[stm32_adc_m0_v1.h:ADC1_TIMER_BASE]`
- `[stm32_adc_m0_v1.h:ADC1_TIMER_PCLK_FREQUENCY]`
- `[stm32_adc_m3m4_v1v2.h:stm32_adcinitialize]`
- `[stm32_adc_m3m4_v1v2.h:adc_io_cmds_e]`
- `[stm32_adc_m3m4_v1v2.h:stm32_adc_resoluton_e]`
- `[stm32_adc_m3m4_v1v2.h:stm32_adc_multimode_e]`
- `[stm32_adc_m3m4_v1v2.h:adc_channel_t]`
- `[stm32_adc_m3m4_v1v2.h:adc_sample_time_s]`
- `[stm32_adc_m3m4_v1v2.h:stm32_adc_dev_s]`
- `[stm32_adc_m3m4_v1v2.h:stm32_adc_ops_s]`
- `[stm32_adc_m3m4_v1v2.h:STM32_ADC_DMAREG_OFFSET]`
- `[stm32_adc_m3m4_v1v2.h:ADC_DMAREG_DMA]`
- `[stm32_adc_m3m4_v1v2.h:STM32_ADC_EXTREG_OFFSET]`
- `[stm32_adc_m3m4_v1v2.h:ADC_EXTREG_EXTSEL_MASK]`
- `[stm32_adc_m3m4_v1v2.h:ADC_EXTREG_EXTSEL_SHIFT]`
- `[stm32_adc_m3m4_v1v2.h:STM32_ADC_JEXTREG_OFFSET]`
- `[stm32_adc_m3m4_v1v2.h:ADC_JEXTREG_JEXTSEL_MASK]`
- `[stm32_adc_m3m4_v1v2.h:ADC_EXTREG_JEXTSEL_SHIFT]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_adc.h:#error]` Compile-time guard: Unsupported STM32 ADC
- `[stm32_adc_m0_v1.h:#error]` Compile-time guard: CONFIG_STM32_ADC1_SAMPLE_FREQUENCY not defined
- `[stm32_adc_m3m4_v1v2.h:#error]` Compile-time guard: CONFIG_STM32_ADC1_SAMPLE_FREQUENCY not defined
- `[stm32_aes.h:#error]` Compile-time guard: Unknown chip for AES
- `[stm32_bbsram.h:#error]` Compile-time guard: Unsupported STM32 stm32_bbsram
- `[stm32_bbsram_m3m4_v1.h:#error]` Compile-time guard: No backup SRAM on this STM32
- `[stm32_can.h:#error]` Compile-time guard: CONFIG_STM32_CAN1_BAUD is not defined
- `[stm32_ccm.h:#error]` Compile-time guard: Unsupported STM32 stm32_ccm
- `[stm32_cordic.h:#error]` Compile-time guard: Unsupported STM32 stm32_cordic
- `[stm32_dac.h:#error]` Compile-time guard: Unsupported STM32 stm32_dac
- `[stm32_dfumode.h:#error]` Compile-time guard: Unsupported STM32 stm32_dfumode
- `[stm32_dma.h:#error]` Compile-time guard: Unsupported STM32 DMA

## Side Effects
- `[stm32_rcc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[stm32_rcc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[stm32_1wire_m3m4_v1.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32_1wire_m3m4_v1.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_1wire_m3m4_v1.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32_1wire_m3m4_v1.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[stm32_1wire_m3m4_v1.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[stm32_1wire_m3m4_v1.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[stm32_adc_m0_v1.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32_adc_m0_v1.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_adc_m0_v1.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32_adc_m0_v1.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)

## Verification
- Run: `make test`
