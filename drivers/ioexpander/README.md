# I/O Expander and GPIO Drivers (`drivers/ioexpander`)

## Overview
Implements the NuttX GPIO upper-half VFS character driver (`/dev/gpio*`), the generic `ioexpander_dev_s`-to-GPIO lower-half adapter, RPMsg remote I/O expander client/server proxies, a dummy test expander, and hardware I2C/SPI I/O expander drivers (AW9523B, CH422G, iC-JX, ISO1H812G, ISO1I813T, MCP23X08, MCP23X17, PCA9538, PCA9555, PCA9557, PCF8574, PCF8575, PI4IOE5V6408, SX1509, TCA64xx).

## Interface
- `gpio.c:gpio_pin_register`, `gpio.c:gpio_pin_register_byname`, `gpio.c:gpio_pin_unregister`, `gpio.c:gpio_pin_unregister_byname` - Registers and unregisters discrete GPIO character devices (`/dev/gpioN` or `/dev/<name>`) supporting `GPIOC_*` `ioctl` commands, `read`, `write`, and `poll`.
- `gpio_lower_half.c:gpio_lower_half`, `gpio_lower_half.c:gpio_lower_half_byname` - Wraps a pin on an `ioexpander_dev_s` instance as a `gpio_dev_s` lower half and registers it with the GPIO character driver.
- `ioe_rpmsg.c:ioe_rpmsg_server_initialize`, `ioe_rpmsg.c:ioe_rpmsg_client_initialize`, `ioe_dummy.c:ioe_dummy_initialize`, `skeleton.c:skel_initialize` - RPMsg remote I/O expander proxy, simulated dummy expander, and template driver.
- `aw9523b.c:aw9523b_initialize`, `ch422g.c:ch422g_initialize`, `mcp23x08.c:mcp23x08_initialize`, `mcp23x17.c:mcp23x17_initialize`, `pca9538.c:pca9538_initialize`, `pca9555.c:pca9555_initialize`, `pca9557.c:pca9557_initialize`, `pcf8574.c:pcf8574_initialize`, `pcf8575.c:pcf8575_initialize`, `pi4ioe5v6408.c:pi4ioe5v6408_initialize`, `sx1509.c:sx1509_initialize`, `sx1509.c:sx1509_leds_initialize`, `tca64xx.c:tca64_initialize` - Initializes I2C I/O expander devices.
- `icjx.c:icjx_initialize`, `iso1h812g.c:iso1h812g_initialize`, `iso1i813t.c:iso1i813t_initialize` - Initializes SPI digital input/output expander devices.

## Invariants
- `gpio.c:gpio_pin_register` and `gpio.c:gpio_pin_register_byname` assert `dev != NULL && dev->gp_ops != NULL`.
- Pin operations on `ioexpander_dev_s` drivers validate that `pin` indices lie within the chip's supported pin count (e.g., `PCA9538_GPIO_NPINS`, `PCA9555_GPIO_NPINS`, `PCA9557_GPIO_NPINS`), returning `-EINVAL` or `-ENXIO` if out of range.
- Expander initializers require non-null bus (`i2c` or `spi`) and configuration pointers (`config != NULL`).

## Side Effects
- Performs I2C (`I2C_TRANSFER`) and SPI (`SPI_SEND`, `SPI_EXCHANGE`) bus transfers to configure pin directions, pull-ups, interrupt masks, and output latches (`mcp23x17.c:mcp23x17_initialize`, `pca9555.c:pca9555_initialize`, `icjx.c:icjx_initialize`).
- Acquires mutexes (`nxmutex_lock`, `nxrmutex_lock`), schedules interrupt bottom-halves on the work queue (`work_queue`), starts polling watchdog timers (`wd_start` in `pcf8574.c:pcf8574_initialize`, `tca64xx.c:tca64_initialize`), and wakes GPIO pollers via `poll_notify` (`gpio.c:gpio_pin_register`).
- Registers `/dev/gpio*` character devices via `register_driver` and allocates driver structures on the kernel heap via `kmm_zalloc` (`gpio.c:gpio_pin_register`, `gpio_lower_half.c:gpio_lower_half`).

## Verification
- Run: `make test`
