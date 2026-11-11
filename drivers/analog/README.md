# Analog Drivers (`drivers/analog`)

## Overview
Provides the upper-half VFS character drivers and chip-specific lower-half/standalone drivers for Analog-to-Digital Converters (ADC), Digital-to-Analog Converters (DAC), analog comparators, operational amplifiers (op-amps), programmable gain amplifiers (PGA), and digital potentiometers.

## Interface
- `adc.c:adc_register` - Registers an ADC character device backed by an `adc_dev_s` lower half with ring-buffered sample FIFO and `poll` notifications.
- `dac.c:dac_register`, `dac.c:dac_txdone` - Registers a DAC character device and notifies the upper half when a DMA or interrupt-driven DAC transmit finishes.
- `comp.c:comp_register`, `opamp.c:opamp_register`, `pot.c:pot_register` - Registers upper-half character devices for comparators, op-amps, and digital potentiometers.
- `ads1115.c:ads1115_initialize`, `ads1242.c:ads1242_register`, `ads1255.c:ads1255_initialize`, `ads7046.c:ads7046_register`, `ads7828.c:ads7828_initialize`, `hx711.c:hx711_register`, `ltc1867l.c:ltc1867l_register`, `max1161x.c:max1161x_initialize`, `mcp3008.c:mcp3008_initialize` - Initializes SPI, I2C, and bit-banged ADC peripheral drivers.
- `ad5410.c:up_ad5410initialize`, `dac7554.c:dac7554_initialize`, `dac7571.c:dac7571_initialize`, `mcp47x6.c:mcp47x6_initialize`, `mcp48xx.c:mcp48xx_initialize` - Initializes SPI and I2C DAC lower-half drivers.
- `lmp92001.c:lmp92001_adc_initialize`, `lmp92001.c:lmp92001_dac_initialize`, `lmp92001.c:lmp92001_gpio_initialize` - Initializes the TI LMP92001 analog monitoring and control system (ADC, DAC, and GPIO expander).
- `mcp445x.c:mcp445x_initialize`, `mcp45xx.c:mcp45xx_initialize`, `pga11x.c:pga11x_initialize`, `pga11x.c:pga11x_select`, `pga11x.c:pga11x_read`, `pga11x.c:pga11x_enable`, `pga11x.c:pga11x_shutdown` - Initializes and controls digital potentiometers and PGA11x programmable gain amplifiers.

## Invariants
- `adc.c:adc_register` asserts `path != NULL && dev != NULL`, `dev->ad_ops != NULL`, `dev->ad_ops->ao_bind != NULL`, and `dev->ad_ops->ao_reset != NULL`.
- `comp.c:comp_register` asserts `dev->ad_ops != NULL`; `ads1255.c:ads1255_initialize` asserts `priv->cb->au_receive != NULL` before delivering conversion results.
- Lower-half initialization functions require non-null bus handles (`i2c != NULL` or `spi != NULL`) and valid channel/gain configuration ranges (e.g., `ads1115.c:ads1115_initialize`, `mcp3008.c:mcp3008_initialize`, `lmp92001.c:lmp92001_gpio_initialize`).
- Upper-half reference counts (`ad_ocount`, `ocount`, `crefs`) must not exceed `255` and gate hardware `setup`/`shutdown` transitions (`adc.c:adc_register`, `dac.c:dac_register`, `hx711.c:hx711_register`).

## Side Effects
- Registers character devices under `/dev` via `register_driver` (`adc.c:adc_register`, `dac.c:dac_register`, `comp.c:comp_register`, `opamp.c:opamp_register`, `pot.c:pot_register`, `ads1242.c:ads1242_register`, `ads7046.c:ads7046_register`, `hx711.c:hx711_register`, `ltc1867l.c:ltc1867l_register`).
- Synchronizes upper-half state and blocking reads/writes using `nxmutex_lock`, `nxsem_wait`, `spin_lock_irqsave`, and `enter_critical_section` (`adc.c:adc_register`, `dac.c:dac_register`, `comp.c:comp_register`, `hx711.c:hx711_register`).
- Performs I2C and SPI bus transfers (`I2C_TRANSFER`, `SPI_SEND`, `SPI_EXCHANGE`), schedules deferred interrupt work via `work_queue` (`ads1255.c:ads1255_initialize`), and wakes pollers via `poll_notify` (`adc.c:adc_register`, `comp.c:comp_register`).

## Verification
- Run: `make test`
