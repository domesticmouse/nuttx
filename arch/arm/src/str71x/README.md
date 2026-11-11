# str71x (`nuttx/arch/arm/src/str71x`)

## Overview
Hardware abstraction and architecture package for `str71x` (STR71x Configuration Options; STR71x Peripheral Selections) under `nuttx/arch/arm/src/str71x`, providing 20 header file(s) and 7 source file(s) (including `chip.h`, `str71x.h`, `str71x_adc12.h`, `str71x_apb.h`).

## Interface
- `[str71x.h:str71x_xtiinitialize]`
- `[str71x.h:str71x_xticonfig]`
- `[str71x.h:str71x_enable_xtiirq]`
- `[str71x.h:str71x_disable_xtiirq]`
- `[str71x.h:str71_spibus_initialize]`
- `[str71x.h:STR71X_CLK2]`
- `[str71x.h:STR71X_PLL1OUT]`
- `[str71x.h:STR71X_PLL2OUT]`
- `[str71x.h:STR71X_CLK3]`
- `[str71x.h:STR71X_RCLK]`
- `[str71x.h:STR71X_PCLK1]`
- `[str71x.h:STR71X_PCLK2]`
- `[str71x_adc12.h:STR71X_ADC12_DATA0]`
- `[str71x_adc12.h:STR71X_ADC12_DATA1]`
- `[str71x_adc12.h:STR71X_ADC12_DATA2]`
- `[str71x_adc12.h:STR71X_ADC12_DATA3]`
- `[str71x_adc12.h:STR71X_ADC12_CSR]`
- `[str71x_adc12.h:STR71X_ADC12_CPR]`
- `[str71x_adc12.h:STR71X_ADC12_SINGLE]`
- `[str71x_adc12.h:STR71X_ADC12_ROUND]`
- `[str71x_adc12.h:STR71X_ADC12_CHANNEL0]`
- `[str71x_adc12.h:STR71X_ADC12_CHANNEL1]`
- `[str71x_adc12.h:STR71X_ADC12_CHANNEL2]`
- `[str71x_adc12.h:STR71X_ADC12_CHANNEL3]`
- `[str71x_apb.h:STR71X_APB_CKDIS_OFFSET]`
- `[str71x_apb.h:STR71X_APB_SWRES_OFFSET]`
- `[str71x_apb.h:STR71X_APB1_CKDIS]`
- `[str71x_apb.h:STR71X_APB1_SWRES]`
- `[str71x_apb.h:STR71X_APB2_CKDIS]`
- `[str71x_apb.h:STR71X_APB2_SWRES]`

## Invariants
- `[str71x_decodeirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[str71x_lowputc.c:#error]` Compile-time configuration constraint: No CONFIG_UARTn_SERIAL_CONSOLE Setting
- `[str71x_prccu.c:#error]` Compile-time configuration constraint: I2C1 requires GPIO0
- `[str71x_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[str71x_serial.c:#error]` Compile-time configuration constraint: No UARTs enabled
- `[str71x_timerisr.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[str71x_timerisr.c:#error]` Compile-time configuration constraint: PCLK2 is too fast for any divisor

## Side Effects
- `[str71x_decodeirq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[str71x_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[str71x_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[str71x_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[str71x_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[str71x_lowputc.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[str71x_prccu.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[str71x_prccu.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[str71x_prccu.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[str71x_serial.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[str71x_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[str71x_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
