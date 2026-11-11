# hardware (`nuttx/arch/arm/src/tlsr82/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/tlsr82/hardware`, providing 14 header file(s) and 0 source file(s) (including `tlsr82_adc.h`, `tlsr82_aes.h`, `tlsr82_analog.h`, `tlsr82_clock.h`).

## Interface
- `[tlsr82_adc.h:ADC_VREF_REG]`
- `[tlsr82_adc.h:ADC_CHAN_REG]`
- `[tlsr82_adc.h:ADC_MODE_REG]`
- `[tlsr82_adc.h:ADC_SAMP0_REG]`
- `[tlsr82_adc.h:ADC_SAMP1_REG]`
- `[tlsr82_adc.h:ADC_SAMP2_REG]`
- `[tlsr82_adc.h:ADC_SAMP3_REG]`
- `[tlsr82_adc.h:ADC_CTRL0_REG]`
- `[tlsr82_adc.h:ADC_CTRL1_REG]`
- `[tlsr82_adc.h:ADC_CLKDIV_REG]`
- `[tlsr82_adc.h:ADC_STATUS_REG]`
- `[tlsr82_adc.h:ADC_DATAL_REG]`
- `[tlsr82_aes.h:AES_CTRL_REG]`
- `[tlsr82_aes.h:AES_DATA_REG]`
- `[tlsr82_aes.h:AES_KEY_REG]`
- `[tlsr82_aes.h:AES_CTRL_CODEC_TRIG]`
- `[tlsr82_aes.h:AES_CTRL_DATA_FEED]`
- `[tlsr82_aes.h:AES_CTRL_CODEC_FINISHED]`
- `[tlsr82_analog.h:ANALOG_ADDR_REG]`
- `[tlsr82_analog.h:ANALOG_DATA_REG]`
- `[tlsr82_analog.h:ANALOG_CTRL_REG]`
- `[tlsr82_clock.h:CPU_CLK]`
- `[tlsr82_clock.h:CLK_EN1_REG]`
- `[tlsr82_clock.h:CLK_EN2_REG]`
- `[tlsr82_clock.h:CLK_EN3_REG]`
- `[tlsr82_clock.h:CLK_SYS_SEL]`
- `[tlsr82_clock.h:CLK_EN1_SPI]`
- `[tlsr82_clock.h:CLK_EN1_I2C]`
- `[tlsr82_clock.h:CLK_EN1_UART]`
- `[tlsr82_clock.h:CLK_EN1_USB]`

## Invariants
- None

## Side Effects
- `[tlsr82_register.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[tlsr82_register.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers

## Verification
- Run: `make test`
