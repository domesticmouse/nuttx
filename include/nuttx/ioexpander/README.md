# I/O Expander & GPIO Subsystem Headers (`include/nuttx/ioexpander`)

## Overview
Defines the NuttX I/O Expander (`ioexpander`) and discrete GPIO character driver (`gpio`) subsystems, providing unified pin direction, option, multi-pin read/write, PWM, and interrupt attachment abstractions, RPMSG remote I/O expander proxies, and hardware driver initializers for I2C/SPI GPIO expander chips.

## Interface
- `ioexpander.h:ioexpander_dev_s`, `ioexpander.h:ioexpander_ops_s`, `ioexpander.h:ioe_pinset_t`, `ioexpander.h:ioe_callback_t` - Core I/O expander device handle, operation vtable (`ioe_direction`, `ioe_option`, `ioe_writepin`, `ioe_readpin`, `ioe_readbuf`, `ioe_multiwritepin`, `ioe_multireadpin`, `ioe_attach`, `ioe_detach`, `ioe_setpwm`), pin bitset type, and interrupt callback.
- `ioexpander.h:IOEXP_SETDIRECTION`, `ioexpander.h:IOEXP_SETOPTION`, `ioexpander.h:IOEXP_WRITEPIN`, `ioexpander.h:IOEXP_READPIN`, `ioexpander.h:IOEXP_READBUF`, `ioexpander.h:IOEXP_MULTIWRITEPIN`, `ioexpander.h:IOEXP_MULTIREADPIN`, `ioexpander.h:IOEXP_SETPWM`, `ioexpander.h:IOEP_ATTACH`, `ioexpander.h:IOEP_DETACH` - Dispatch macros for I/O expander operations.
- `gpio.h:gpio_dev_s`, `gpio.h:gpio_operations_s`, `gpio.h:gpio_pintype_e`, `gpio.h:gpio_signal_s`, `gpio.h:pin_interrupt_t`, `gpio.h:gpio_pin_register`, `gpio.h:gpio_pin_register_byname`, `gpio.h:gpio_pin_unregister`, `gpio.h:gpio_pin_unregister_byname`, `gpio.h:gpio_lower_half`, `gpio.h:gpio_lower_half_byname`, `gpio.h:GPIOC_WRITE`, `gpio.h:GPIOC_READ`, `gpio.h:GPIOC_PINTYPE`, `gpio.h:GPIOC_REGISTER`, `gpio.h:GPIOC_SETPINTYPE` - Single-pin GPIO character driver framework and I/O-expander-to-GPIO lower-half adapter.
- `ioe_dummy.h:ioe_dummy_initialize`, `ioe_rpmsg.h:ioe_rpmsg_server_initialize`, `ioe_rpmsg.h:ioe_rpmsg_client_initialize` - Simulated dummy I/O expander and RPMSG cross-core I/O expander client/server initializers.
- `aw9523b.h:aw9523b_initialize`, `ch422g.h:ch422g_initialize`, `icjx.h:icjx_initialize`, `iso1h812g.h:iso1h812g_initialize`, `iso1i813t.h:iso1i813t_initialize`, `mcp23x08.h:mcp23x08_initialize`, `mcp23x17.h:mcp23x17_initialize`, `pca9538.h:pca9538_initialize`, `pca9555.h:pca9555_initialize`, `pca9557.h:pca9557_initialize`, `pcf8574.h:pcf8574_initialize`, `pcf8575.h:pcf8575_initialize`, `pi4ioe5v6408.h:pi4ioe5v6408_initialize`, `sx1509.h:sx1509_initialize`, `sx1509.h:sx1509_leds_initialize`, `tca64xx.h:tca64_initialize` - External I2C/SPI I/O expander chip driver initializers.

## Invariants
- `ioexpander.h:ioe_pinset_t` width scales with `CONFIG_IOEXPANDER_NPINS` (`uint8_t` for `<=8`, `uint16_t` for `<=16`, `uint32_t` for `<=32`, `uint64_t` for `<=64`).
- `gpio.h:gpio_dev_s` bounds registered signal recipients to `CONFIG_DEV_GPIO_NSIGNALS` and `poll()` waiters to `CONFIG_DEV_GPIO_NPOLLWAITERS`.

## Side Effects
- `gpio.h:gpio_pin_register`, `gpio.h:gpio_pin_register_byname`, `gpio.h:gpio_lower_half`, and `sx1509.h:sx1509_leds_initialize` register character device nodes in the VFS.
- `ioexpander.h:ioexpander_ops_s` methods and chip initializers perform I2C/SPI bus transactions or RPMSG IPC messages to configure and drive physical GPIO expander pins and interrupts.

## Verification
- Run: `make test`
