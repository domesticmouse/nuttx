# Analog Subsystem Headers (`include/nuttx/analog`)

## Overview
Provides the upper-half and lower-half interfaces, FIFO queues, `ioctl` command definitions, and peripheral chip initialization declarations for NuttX Analog-to-Digital Converters (ADC), Digital-to-Analog Converters (DAC), Analog Comparators (`comp`), Operational Amplifiers (`opamp`), Programmable Gain Amplifiers (`pga11x`), and Digital Potentiometers (`pot`).

## Interface
- `adc.h:adc_dev_s`, `adc.h:adc_ops_s`, `adc.h:adc_callback_s`, `adc.h:adc_msg_s`, `adc.h:adc_fifo_s`, `adc.h:adc_register` - Core ADC device structures, lower-half vtable, upper-half receive callback interface, sample FIFO, and character driver registration.
- `dac.h:dac_dev_s`, `dac.h:dac_ops_s`, `dac.h:dac_msg_s`, `dac.h:dac_fifo_s`, `dac.h:dac_info_s`, `dac.h:dac_register`, `dac.h:dac_txdone` - Core DAC device structures, transmit FIFO, DMA configuration types, and registration APIs.
- `comp.h:comp_dev_s`, `comp.h:comp_ops_s`, `comp.h:comp_callback_s`, `comp.h:comp_register` - Analog comparator upper/lower-half driver interface and VFS registration.
- `opamp.h:opamp_dev_s`, `opamp.h:opamp_ops_s`, `opamp.h:opamp_register` - Operational amplifier driver structures and VFS registration.
- `pot.h:pot_dev_s`, `pot.h:pot_ops_s`, `pot.h:pot_info_s`, `pot.h:pot_wiper_s`, `pot.h:pot_register`, `pot.h:mcp445x_initialize`, `pot.h:mcp45xx_initialize` - Digital potentiometer driver framework and Microchip MCP445x/MCP45xx initializers.
- `ioctl.h:ANIOC_TRIGGER`, `ioctl.h:ANIOC_WDOG_UPPER`, `ioctl.h:ANIOC_WDOG_LOWER`, `ioctl.h:ANIOC_GET_NCHANNELS`, `ioctl.h:ANIOC_RESET_FIFO`, `ioctl.h:ANIOC_DAC_DMA_START`, `ioctl.h:ANIOC_COMP_ENABLE` - Shared analog subsystem `ioctl` command codes and per-device command range allocations.
- `ads1115.h:ads1115_initialize`, `ads1242.h:ads1242_register`, `ads7046.h:ads7046_register`, `ads7828.h:ads7828_ref_e`, `hx711.h:hx711_register`, `lmp92001.h:lmp92001_gpio_initialize`, `ltc1867l.h:ltc1867l_register`, `max1161x.h:max1161x_ref_e`, `mcp3008.h:mcp3008_initialize`, `mcp445x.h:mcp445x_tcon_s`, `mcp47x6.h:mcp47x6_command_e`, `mcp48xx.h:mcp48xx_gain_select_e`, `pga11x.h:pga11x_initialize` - Device-specific ADC, DAC, load-cell amplifier, and PGA driver interfaces.

## Invariants
- `adc.h:CONFIG_ADC_FIFOSIZE` is clamped to at most `65535` (`uint16_t` index range), and `dac.h:CONFIG_DAC_FIFOSIZE` is clamped to at most `255` (`uint8_t` index range).
- `adc.h:adc_dev_s` and `dac.h:dac_dev_s` require non-null `ad_ops` pointers before calling `adc_register` or `dac_register`, and synchronize concurrent access via `ad_lock` (`mutex_t`) and `ad_spinlock` (`spinlock_t`).

## Side Effects
- `adc.h:adc_register`, `dac.h:dac_register`, `comp.h:comp_register`, `opamp.h:opamp_register`, `pot.h:pot_register`, and `hx711.h:hx711_register` register character devices in the VFS and initialize synchronization primitives.
- Lower-half operations (`ADC_SETUP`, `ADC_RXINT`, `ADC_IOCTL`, `ao_send`, `po_setwiper`, etc.) perform SPI/I2C bus transfers or MMIO register writes and configure hardware interrupts/DMA.

## Verification
- Run: `make test`
