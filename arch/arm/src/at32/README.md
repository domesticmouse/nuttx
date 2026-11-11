# at32 (`nuttx/arch/arm/src/at32`)

## Overview
Hardware abstraction and architecture package for `at32` (AT32 Configuration Options; AT32 Peripheral Support) under `nuttx/arch/arm/src/at32`, providing 33 header file(s) and 49 source file(s) (including `at32.h`, `at32_adc.h`, `at32_can.h`, `at32_dbgmcu.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/at32/hardware`, providing 26 header file(s) and 0 source file(s) (including `at32_adc.h`, `at32_adc_v1.h`, `at32_can.h`, `at32_dbgmcu.h`).

## Interface
- `[at32_adc.h:at32_adcinitialize]`
- `[at32_adc.h:adc_io_cmds_e]`
- `[at32_adc.h:at32_adc_resoluton_e]`
- `[at32_adc.h:at32_adc_multimode_e]`
- `[at32_adc.h:adc_channel_t]`
- `[at32_adc.h:adc_sample_time_s]`
- `[at32_adc.h:at32_adc_dev_s]`
- `[at32_adc.h:at32_adc_ops_s]`
- `[at32_adc.h:AT32_ADC_DMAREG_OFFSET]`
- `[at32_adc.h:ADC_DMAREG_DMA]`
- `[at32_adc.h:AT32_ADC_EXTREG_OFFSET]`
- `[at32_adc.h:ADC_EXTREG_EXTSEL_MASK]`
- `[at32_adc.h:ADC_EXTREG_EXTSEL_SHIFT]`
- `[at32_adc.h:AT32_ADC_JEXTREG_OFFSET]`
- `[at32_adc.h:ADC_JEXTREG_JEXTSEL_MASK]`
- `[at32_adc.h:ADC_EXTREG_JEXTSEL_SHIFT]`
- `[at32_adc.h:AT32_ADC_ISR_OFFSET]`
- `[at32_adc.h:AT32_ADC_IER_OFFSET]`
- `[at32_adc.h:ADC_EXTREG_EXTEN_MASK]`
- `[at32_adc.h:ADC_EXTREG_EXTEN_NONE]`
- `[at32_can.h:at32_caninitialize]`
- `[at32_can.h:at32_cansockinitialize]`
- `[at32_can.h:CONFIG_AT32_CAN_TSEG1]`
- `[at32_can.h:CONFIG_AT32_CAN_TSEG2]`
- `[at32_dma.h:at32_dmachannel]`
- `[at32_dma.h:at32_dmafree]`
- `[at32_dma.h:at32_dmasetup]`
- `[at32_dma.h:at32_dmastart]`
- `[at32_dma.h:at32_dmastop]`
- `[at32_dma.h:at32_dmaresidual]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[at32_adc.h:#error]` Compile-time guard: CONFIG_AT32_ADC1_SAMPLE_FREQUENCY not defined
- `[at32_can.h:#error]` Compile-time guard: CONFIG_AT32_CAN1_BAUD is not defined
- `[at32_gpio.h:#error]` Compile-time guard: Unrecognized AT32 chip
- `[at32_pwm.h:#error]` Compile-time guard: CONFIG_AT32_TIM1_CHANNEL must be provided
- `[at32_rcc.h:#error]` Compile-time guard: Unsupported AT32 chip
- `[at32_uart.h:#error]` Compile-time guard: Unsupported AT32 UART
- `[at32_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[at32_adc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[at32_adc.c:#error]` Compile-time configuration constraint: AT32 ADC IP version not specified
- `[at32_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[at32_allocateheap.c:#error]` Compile-time configuration constraint: CONFIG_MM_REGIONS > 2 but I don't know what some of the region(s) are
- `[at32_can.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[at32_rcc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[at32_rcc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[at32_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[at32_adc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[at32_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[at32_adc.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[at32_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[at32_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[at32_adc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[at32_can.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[at32_can.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[at32_can.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
